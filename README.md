# WordPress-Plugin-Framework

My own framework for making the WordPress plugins the way I do.

The main plugin class is a Singleton pattern to ensure that only one instance created.

Includes blank methods for activation, deactivation, and registering scripts and styles.

The base class sets up the text domain for internationalization and localization. Just drop your i18n and l10n files into the lang directory.

A blank uninstall file is included and setup correctly to make sure it is only called from the WordPress dashboard.

Additional methods and classes will be built out as I get to them to further simplify the various WordPress APIs I use.

## Custom Post Types

You can create a custom post type through the CustomPostType object. The class accepts optional arguments for post capabilities (array), post support ( array ), and menu icon (string). If nothing is specified they are set to the WordPress default

Create new custom post types in the main plugin class constructor.

Ex.: $new_post_type = new Custom_Post_Type( $plural_post_type_name, $capabilities, $support, $menu_icon );

## Taxonomies

Taxonomies can be added to post types by creating a Custom_Taxonomy object. The $post_types parameter is options and will use "post" if not specified, it will accept a string or array of strings.

Ex.: $new_taxonomy = new Custom_Taxonomy( $plural_taxonomy_name, $post_types );

### Terms

You can add terms to a Custom_Taxonomy object by using the add_terms() method. It accepts a single parameter that can either be a string or array of strings.

Ex.: $new_taxonomy->add_terms( $terms );

## Helper Functions

Some helper functions are included in the main plugin class. They are public, static functions so can be used anywhere.

### print_to_log()

Writes a message to debug.log in the wp-content folder if you have the wp-config.php setup to do that. It will accept any variable or string.

Ex.: WordPress_Plugin_Framework::print_to_log( $message_to_send ).

### make_singular()

Takes a plural string and makes it singular.

Ex.: $singular_string = WordPress_Plugin_Framework::make_singular( $plural_string );