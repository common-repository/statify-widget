=== Statify Widget ===
Contributors: 		bitnulleins
Tags: 			    statify, widget, popular posts, custom post types, wordpress, analytics, privacy, statistics
Requires at least: 	4.6
Tested up to: 		6.1.1
Requires PHP: 		5.2.4
Stable tag: 		trunk
License: 		    GPLv2 or later
License URI: 		http://www.gnu.org/licenses/gpl-2.0.html

Widget for list popular content (pages, posts, custom post types) – based on Statify plugin.

== Description ==

The *Statify Widget* shows the most popular content from [Statify](http://wordpress.org/plugins/statify/) plugin made by pluginkollektiv. Fast and clear!

= What is Statify? =

Statify is a plugin for visitor statistics with emphasis on privacy, transparency and clarity.

**Note**: This widget only works with the main plugin [Statify](http://wordpress.org/plugins/statify/).

= Features =

* **Popular Posts**: Sum up all view from Statify and put it together in a widget
* **Shortcodes**: The counter for each post/page can be put everywhere
* **Custom Post Types**: Statify Widget supports custom post types, that can be displayed
* **Intelligent summary**: Once there are different paths to a content, the widget adds them together 
* **Period Selectable**: It is possible to choose an individual daily period for the post popular content
* **New: Custom Widget Template**: Now, you can add individual post/page paramater to widget template (see FAQ)

= Shortcode =

The shortcode `[statify-count]` can be used to display calls to the current post or page. With the options "prefix" and "suffix" displayed texts can be checked before (prefix) and after (suffix) the calls:

`[statify-count prefix="Total " suffix=" calls." days="8"]`

Parameter:

* `prefix` Sentence before views
* `suffix` Sentence after views
* `days` Inteval for view statistics

Result: A total of 243 views.

= Widget Settings =

The following settings can be made in the widget:

* Title
* Content Type (Default: post )
* Category (when content type post is select)
* Amount of entries (default: 5)
* Show views (default: No)
* Custom text (Replace variable for views: %VIEWS%)
* Number of past days (0 days = all statistics)

= Support =

Friendly questions about the widget I like to answer under [Support](https://wordpress.org/support/plugin/statify-widget/). 

If you like my work and want to support *me*, feel free to [rate](https://de.wordpress.org/plugins/statify-widget/#reviews) this plugin!

= Author =

* Finn Dohrn
* [Homepage](http://www.bit01.de)

== Installation ==

1. Install the "[Statify](http://wordpress.org/plugins/statify/)" by pluginkollektiv.
1. Install this Plugin "Statify Widget" and activate it.
1. Activate the *Popular Post Widget* under widgets.

== Frequently Asked Questions ==

= Error: The widget does not find any entries =

Statify has not added statistics yet. Wait some days to collect some statistics by Statify.

= Show pages and posts together =

Yes! Since 1.1.4 that works.

Just in the content type widget: select *Pages and posts*. He then displays the default content types "post" and "page" together.

= Show views in pages and posts =

This is possible with shortcodes. Specifying a prefix and suffix is ​​not mandatory:

Properties:

* `days` = Amount of days
* `prefix`= Text before the view count
* `suffix`= Text after the view count

Shortcode: 

`[statify-count prefix ="Total" suffix ="calls." days="8"]`

The total view counter for the whole webpage:

`[statify-count-sum prefix="Total" suffix="calls."]`

= I do not have static page as homepage =

No problem. A pseudo "Frontpage" (with views) entry appears.

= I changed the permalink structure =

This changes nothing. The plugin takes every Statify entry and adds it together.

= Change design (CSS) =

Just use these CSS classes:
* List: `.statify-widget-list {...}`
* List item: `.statify-widget-element {...}`
* List item view counter: `.statify-widget-element span {...}`
* List item link: `.statify-widget-link {...}`

= Change list from numeric to points =

If you want to change the list of contents (1st, 2nd, 3rd, ...) to bullets, just add the following to your CSS:

`.statify-widget-element {
    list-style-type: circle;
} `

= ADVANCED: Change Widget Template =

Since 1.3.8 it is possible to customize the Widget Template by adding code to your Template `functions.php`. You can use the [WP Post Object](https://developer.wordpress.org/reference/classes/wp_post/) in the template.

There exists two hooks:

* `statify_widget_before_link`
* `statify_widget_after_link`

For Example add thumbnail before link in a div:

`
function statify_custom_template($post) {
	echo '<div class="post_thumbnail">'. get_the_post_thumbnail($post->ID, 'thumb') .'</div>';
}

add_action('statify_widget_before_link', 'statify_custom_template');
`

= ADVANCED: Return all posts as WP Query =

For example put this in your theme:

`
<?php
    if(function_exists('statify_popular_posts')) {
        &#36;wp_query = statify_popular_posts(
            &#36;amount = 5,
            &#36;days = 30,
            &#36;post_type = 'post',
            &#36;post_category = 0
        );
        
        // Make WP Post loop...
        while ( &#36;wp_query->have_posts() ) {
                &#36; wp_query->the_post();
        }
    }
?>
`

Properties

* `&#36;days` = Range of days for statictics (0 = all days)
* `&#36;amount` = Amount of posts
* `&#36;post_type` = Post type ("post", "page", ...)
* `&#36;post_category` = Category of the post, if post type is choosen

== Screenshots ==

1. Statify Widget Result
2. Statify Widget Settings


== Changelog ==

= 1.3.8 =

* Hot-Fix: Update problem, that hide any popular post widget content.
* Remove unnecessary JQuery.

= 1.3.7 =

* Add missing PHP Class File.

= 1.3.5 =

* Feature Request: Add custom template option for widget (See: https://wordpress.org/support/topic/add-thumbnails-and-disable-jquery/)

= 1.3.4 =

* Fix problem with Widget settings in Elementor (See: https://wordpress.org/support/topic/anzahl-der-aufrufe-anzeigen/)

= 1.3.3 =

* New way to return list of popular posts as WP_Query
* Correct the way how pseudo frontpage is generate

= 1.3.2 =

* Fix for non existing views in "Frontpage" alias

= 1.3.1 =

* Fix bug in [statify-count-sum]. Remove unnecessary post_id.
* Add shortcode parameter "days" for limit interval days.

= 1.3.0 =

* Bugfix: Hide duplicate frontpage item in widget.

= 1.2.9. =

* Now comtaible with PHP8
* Fix two bugs occured in PHP8 version.
* Remove "frontpage" label, now the frontpage list with its original page name

= 1.2.8 =

* Fix bugs

= 1.2.7 =

* Add some description and tested up to WordPress v5.6

= 1.2.5 =

* Fixed bug in backend for category select

= 1.2.4 =

* Fixed ressourcen bug. Add required java script folder.

= 1.2.3 =

* Add feature to filter for post category in widget.

= 1.2.2 =

* Fixed another bug for unpublished posts

= 1.2.1 =

* Translate whole plugin into English.
* Fixed "show views" translation bug.

= 1.2 =

* English and German language
* Fixed a link bug in the widget
* Shortcode for total number of views

= 1.1.9 =

* Correction of a translation error.
* List type setting has been removed.

= 1.1.8 =

* The plugin is now ready for translation.
* You can now choose between the list type (`<ol>` or `<ul>`) per widget.
* Now the classes `statify-widget-list`,` statify-widget-element` and `statify-widget-link` have been added as class to make a more flexible design possible.

= 1.1.7 =

* List type ordered (`<ol>`) changed to unordered (`<ul>`) for higher theme compatibility.
* Outdated create_function () method swapped.
* Bug with shotcode usage removed (statify_count edited in Statify_Posts.class.php)

= 1.1.6 =

* The functionality of restricting a time period for the content has been added.
* Fixed a bug that caused the homepage to ignore when choosing "Posts + Pages".

= 1.1.5 =

* An error has been removed. He had always shown the number of views at the end of a page.

= 1.1.4 =

* Content Type: "Posts and Pages" added to show together
* Views for article shortcode and theme function

= 1.1.3 =

* Recording the evolution and tested for WordPress 4.7.6

= 1.1.2 =
* Corrections in the validation

= 1.1.1 =
* Custom text for the number of views
* Unused require_once () removes
* span element added by the number of views

= 1.1 =
* Limitation of records canceled
* added title attribute to the links

= 1.0 =
* Release of the first version

== Upgrade Notice ==

No Upgrades