## $${\color{red}WORDPRESS \ Cheatsheet}$$

### Theme Headers style.css

/\*\*

\* Theme Name: My theme (required)

\* Template: The name of the parent theme. E.g. Twenty Twenty

\* Description: A short description of the theme.

\* Theme URI: Subject URL. E.g. http://wordpress.org/themes/twentytwenty

\* Author: Keny

\* Author URI: https://keny.studio

\* Tags: black, brown, orange

\* Text Domain: Subject translation domain. E.g. twentythirteen

\* License: License. E.g. GNU General Public License v2 or later

\* License URI: http://www.gnu.org/licenses/gpl-2.0.html

\* Version: 1.0

\*/

### .htaccess code

 BEGIN WordPress

 The directives (lines) between "BEGIN WordPress" and "END WordPress" are

 dynamically generated, and should only be modified via WordPress filters.

 Any changes to the directives between these markers will be overwritten.

 <br>

<IfModule mod\_rewrite.c>

RewriteEngine On

RewriteRule .\* - [E=HTTP\_AUTHORIZATION:%{HTTP:Authorization}]

RewriteBase /

RewriteRule ^index\.php$ - [L]

RewriteCond %{REQUEST\_FILENAME} !-f

RewriteCond %{REQUEST\_FILENAME} !-d

RewriteRule . /index.php [L]

</IfModule>

END WordPress

### ****The files (includes)****

| Function | File |
| --- | --- |
| \<?php get\_header(); ?> | header.php |
| \<?php get\_template\_part('file'); ?> | file.php |
| \<?php get\_search\_form(); ?> | searchform.php |
| \<?php comments\_template(); ?> | comments.php |
| \<?php get\_sidebar(); ?> | sidebar.php |
| \<?php get\_footer(); ?> | footer.php |

### ****Theme Path Functions****

| Function | Description |
| --- | --- |
| get\_template\_directory() | The path to the parent theme (not child). No trailing /. |
| get\_stylesheet\_directory() | Theme path (where parent/child style.css). No trailing /. |
| get\_parent\_theme\_file\_path() | File path of parent theme (not child). |
| get\_theme\_file\_path() | File path of parent/child theme. |
| load\_template() | Includes file (require\_once). |
| locate\_template() | Finds/includes parent/child theme file. |

### ****Theme URL Functions****

| Function | Description |
| --- | --- |
| get\_template\_directory\_uri() | URL of parent theme (not child). No trailing /. |
| get\_stylesheet\_directory\_uri() | Theme URL (child theme if it exists). No trailing /. |
| get\_theme\_root\_uri() | URL of the theme's DIR. No trailing /. |
| get\_stylesheet\_uri() | URL of the theme's style.css file. |
| get\_theme\_file\_uri() | URL of the parent/child theme file. |
| get\_parent\_theme\_file\_uri() | URL of the parent theme file. |

### ****Theme Files (Hierarchy) /themes/THEME/****

| File | Description |
| --- | --- |
| style.css | Theme styles file (required) |
| index.php | Any page without a template file (required) |
| front-page.php | Front (Home) page |
| home.php | Posts page (or Home page) |
| functions.php | A special file for PHP functions (code) |
| 404.php | Page "not found" |
| comments.php | Comments template (part) |
| header.php | Site header template (part) |
| searchform.php | Search form template (part) |
| sidebar.php | Sidebar template (part) |
| footer.php | Site footer template (part) |
| single.php | Post page, post\_type = post |
| single-POST\_TYPE.php | Post page, post\_type = POST\_TYPE |
| single-POST\_TYPE-POST\_NAME.php | Post page with POST\_NAME and POST\_TYPE |
| singular.php | Post of any post type |
| page.php | Page, post\_type = page |
| page-POST\_NAME.php | Page, post\_name = POST\_NAME |
| page-ID.php | Page, ID = ID |
| attachment.php | Any attachment page |
| image.php | Image attachment page |
| archive.php | Page of any archive |
| archive-POST\_TYPE.php | Page of post type archive |
| search.php | Search page |
| category.php | Any category page |
| category-SLUG.php | Category page with slug = SLUG |
| category-ID.php | Category page with term\_id = ID |
| tag.php | Any tag page |
| tag-SLUG.php | Tag page with slug = SLUG |
| tag-ID.php | Tag page with term\_id = ID |
| taxonomy.php | Any custom taxonomy element page |
| taxonomy-TAXONOMY.php | Page of any term of TAXONOMY taxonomy |
| taxonomy-TAXONOMY-SLUG.php | Page of SLUG term of TAXONOMY taxonomy |
| author.php | Page of author posts |

### A post template from any file:

\<?php

/\*

Template Name: My page template

Template Post Type: post, page, product

\*/

// … template file code

### ****Site Information –**** bloginfo()

| Function | Description |
| --- | --- |
| bloginfo() | Displays information about the site. |
| get\_bloginfo() | Gets information about the site. |
| \<?php bloginfo('name'); ?> | Site name. |
| \<?php bloginfo('description'); ?> | Short description of the site. |
| \<?php bloginfo('template\_url'); ?> | Theme URL (get\_template\_directory()). |
| \<?php bloginfo('template\_directory'); ?> | Same as template\_url. |
| \<?php bloginfo('stylesheet\_directory'); ?> | Theme URL (get\_stylesheet\_directory\_uri()). |
| \<?php bloginfo('stylesheet\_url'); ?> | Theme file style.css URL (get\_stylesheet\_uri()). |
| \<?php bloginfo('charset'); ?> | Site encoding (UTF-8). |
| \<?php bloginfo('html\_type'); ?> | Content-Type of the page (text/html). |
| \<?php bloginfo('language'); ?> | Site locale (language), e.g., RU. |
| \<?php bloginfo('version'); ?> | WordPress version, e.g., 5.5.3. |
| \<?php bloginfo('rss2\_url'); ?> | URL of the feed (/feed). |
| \<?php bloginfo('comments\_rss2\_url'); ?> | URL of the comments feed (/comments/feed). |
| \<?php bloginfo('admin\_email'); ?> | Admin email. |
| \<?php bloginfo('pingback\_url'); ?> | Notification URL to xmlrpc.php. |
| \<?php bloginfo('rdf\_url'); ?> | RDF/RSS 1.0 feed URL (/feed/rdf). |
| \<?php bloginfo('rss\_url'); ?> | RSS 0.92 feed URL (/feed/rss). |
| \<?php bloginfo('atom\_url'); ?> | Atom feed URL (/feed/atom). |
| \<?php bloginfo('url'); ?> | Home page URL (alias home\_url()). |
| \<?php bloginfo('wpurl'); ?> | Admin panel URL (alias site\_url()). |

### ****Comment Loop****

| Function | Description |
| --- | --- |
| comment\_ID() | Displays the ID of the current comment. |
| comments\_popup\_link() | Displays \<a> link to the comment popup. |
| comment\_text() | Displays the text of the comment. |
| comment\_author() | Displays the comment author name. |
| comments\_link() | Displays a URL to the post comment form. |
| comment\_reply\_link() | Displays an \<a> link to reply to comments. |
| comment\_time() | Displays the comment publishing time. |
| comment\_author\_link() | Displays the comment author's name as a link. |
| comment\_author\_url() | Displays comment author URL (set when commenting). |
| comment\_author\_url\_link() | Displays comment author link (A tag). |
| comment\_author\_email\_link() | Displays comment author email as a mailto link. |
| edit\_comment\_link() | Displays edit comment link. |

### ****The Loop****

| Function | Description |
| --- | --- |
| in\_the\_loop() | Checks if the WordPress loop is active. |
| have\_posts() | Checks if there are posts for the loop. |
| the\_post() | Sets the next post in the loop and global $post. |
| setup\_postdata() | Sets global $post. |
| the\_ID() | Displays the ID of the current post. |
| the\_title() | Displays current post title. |
| the\_title\_attribute() | Displays post title for HTML tag attribute. |
| the\_content() | Displays post content. |
| the\_excerpt() | Displays the excerpt (quote) of the post, with [...] at the end. |
| the\_excerpt\_rss() | Displays the excerpt (quote) for RSS. |
| get\_permalink() | Gets post URL. |
| the\_permalink() | Displays post URL. |
| comments\_number() | Displays post's number of comments. |
| edit\_post\_link() | Displays edit post link (A HTML tag). |
| the\_date() | Displays/retrieves post publication date. |
| get\_the\_date() | Gets the post creation date. |
| the\_time() | Displays post publication time. |
| get\_post\_time() | Gets time (date) of post publication. |
| the\_modified\_date() | Displays time (date) when post was changed. |
| the\_post\_thumbnail() | Displays HTML code of post thumbnail image. |
| get\_post\_thumbnail\_id() | Gets the post thumbnail ID. |
| has\_post\_thumbnail() | Conditional: whether or not the post has a thumbnail. |
| the\_post\_thumbnail\_url() | Displays the URL of the post thumbnail. |
| the\_attachment\_link() | Displays the link (A tag) of the attachment or attachment page. |
| get\_attachment\_link() | Gets the URL to the attachment page. |
| wp\_get\_attachment\_link() | Gets the link (A tag) of the attachment or attachment page. |
| the\_tags() | Displays links to the post tags. |
| the\_category() | Displays post categories as links. |
| the\_taxonomies() | Displays links (\<a>) to the post terms. |
| in\_category() | Checks if the post belongs to a category. |
| sticky\_class() | Displays a "sticky" class if it is a sticky post. |
| is\_sticky() | Checks if the post is sticky to the home page. |
| the\_meta() | Displays post meta-fields in \<li> list. |
| get\_post\_format() | Gets the post format: quote, status, video, audio. |
| the\_author() | Displays post's author name. |
| get\_the\_author() | Gets post's author name (display\_name). |
| the\_author\_link() | Displays link (A tag) to the site of post's author. |
| get\_the\_author\_link() | Gets link (A tag) to the site of post's author. |
| the\_author\_posts() | Displays the total number of posts written by the author. |
| the\_author\_posts\_link() | Displays link (A tag) to the post author's archive page. |
| the\_author\_meta() | Displays specified meta-field of the post author (WP user). |
| get\_the\_author\_meta() | Gets specified meta-field of the post author (WP user). |
| the\_modified\_author() | Displays the name of the author who last modified the post. |

\<?php if ( have\_posts() ) : while ( have\_posts() ) : the\_post(); ?>

\<!-- Post output, loop functions: the\_title(), etc. -->

\<?php endwhile; else: ?>

No posts.

\<?php endif; ?>

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\<?php if ( have\_posts() ){ while ( have\_posts() ){ the\_post(); ?>

\<!-- Post output, loop functions: the\_title(), etc. -->

\<?php } } else { ?>

No posts.

\<?php } ?>

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\<?php while ( have\_posts() ){ the\_post(); ?>

\<!-- Post output, loop functions: the\_title(), etc. -->

\<?php } ?>

\<?php if ( ! have\_posts() ){ ?>

No posts.

\<?php } ?>

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\<?php

global $post;

$myposts = get\_posts([

'numberposts' => 5,

'offset' => 1,

'category' => 1

]);

if( $myposts ){

foreach( $myposts as $post ){

setup\_postdata( $post );

?>

<!-- Post output, loop functions: the\_title(), etc. -->

\<?php

}

} else {

// No posts found

}

wp\_reset\_postdata(); // Reset $post

?>

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\<?php

global $post;

$query = new WP\_Query( [

'posts\_per\_page' => 5,

'orderby' => 'comment\_count',

] );

if ( $query->have\_posts() ) {

while ( $query->have\_posts() ) {

$query->the\_post();

?>

<!-- Post output, loop functions: the\_title(), etc. -->

\<?php

}

} else {

// No posts found

}

wp\_reset\_postdata(); // Reset $post

?>

### ****WP-CLI****

| Command | Description |
| --- | --- |
| wp core download --locale=pl\_PL | Download WordPress in Polish locale. |
| wp core config --dbname=NAME --dbuser=USER --dbpass=PASS --dbprefix=wp\_ | Generate wp-config.php. |
| wp db create | Create database (based on wp-config.php). |
| wp core install --url=example.com --title=Example --admin\_user=supervisor --admin\_email=info@example.com –admin\_password=strongpassword | Install WordPress to created DB. |
| wp post list | List all posts. |
| wp post edit 1 | Edit post with ID 1. |
| wp post update 1 --post\_title="Your New title..." | Update post ID 1 title. |
| wp post create --post\_status=publish --post\_title="Second Post" –edit | Create a new post and edit it. |
| wp post meta list 18 | List all metas of post ID 18. |
| wp post meta get 18 meta\_name | Get value of meta meta\_name for post 18. |
| wp post meta delete 18 meta\_name | Delete meta meta\_name from post 18. |
| wp db export - --add-drop-table --default-character-set=utf8mb4 \| gzip > ./db-dump-$(date +%Y-%m-%d-%H%M%S).sql.gz | Create DB dump with timestamp. |
| wp db import db\_backup-2022-01-20.sql | Import DB dump into database. |
| wp db cli | Open WordPress DB in CLI. |
| wp db query "SELECT user\_login, ID FROM wp\_users;" | Run SQL query on WP DB. |
| wp db optimize | Optimize database. |
| wp core update | Update WordPress core. |
| wp plugin update –all | Update all plugins. |
| wp plugin list | List all installed plugins. |
| wp plugin search yoast | Search for a plugin (example: Yoast). |
| wp plugin install yoast | Install a plugin (example: Yoast). |
| wp theme list | List all installed themes. |
| wp theme install twentyone | Install a theme (example: Twenty Twenty-One). |
| wp theme activate twentyone | Activate a theme. |

### Plugin Headers

\<?php

/\*\*

\* Plugin Name: My Plugin

\* Description: Description of the plugin (140 characters)

\* Plugin URI: URL to info about plugin

\* Author URI: https://keny.studio

\* Author: Keny

\* Text Domain: Translation ID. E.g. my-plugin

\* Domain Path: Path to MO file (relative to plugin folder)

\* Requires PHP: 7.0

\* Requires at least: 5.7

\* License: GPL2

\* License URI: https://www.gnu.org/licenses/gpl-2.0.html

\* Network: true - activates the plugin for the whole network

\* Update URI: https://example.com/link\_to\_update

\* Requires Plugins: some-plugin, some-plugin-2

\* Version: 1.0

\*/

// plugin code

### ****Plugin Management Functions****

| Function | Description |
| --- | --- |
| register\_activation\_hook() | Registers the function to activate the plugin. |
| register\_deactivation\_hook() | Registers the function to deactivate the plugin. |
| register\_uninstall\_hook() | Registers the function for deleting the plugin. |
| plugins\_url() | Gets URL of plugins/mu-plugins folder (no trailing slash). |
| plugin\_basename() | Path to the plugin file (from the plugins folder). |
| plugin\_dir\_path() | Gets the path to the plugin folder (with trailing slash). |
| plugin\_dir\_url() | Gets the URL of the plugin folder (with trailing slash). |
| get\_plugins() | Gets data of plugins (both active and inactive). |
| get\_plugin\_data() | Gets data of the plugin from file headers. |
| activate\_plugins() | Activates plugins. |
| deactivate\_plugins() | Deactivates plugins. |
| is\_plugin\_active() | Checks if a plugin is active (works only in the admin panel). |

\<?php

if( ! defined('WP\_UNINSTALL\_PLUGIN') ) exit;

// the check passed successfully. Starting from here remove all plugin data (options, db tables etc.).

delete\_option( 'plug\_option' );

### ****Script & Style Functions****

| Function | Description |
| --- | --- |
| wp\_register\_script() | Registers the JS file. |
| wp\_enqueue\_script() | Registers and connects the JS file. |
| wp\_dequeue\_script() | Deletes the JS file from the output queue. |
| wp\_add\_inline\_script() | Adds inline JS code to the registered script. |
| wp\_deregister\_script() | Unregisters the JS file. |
| wp\_script\_add\_data() | Adds data to the script (e.g., for specific browsers like "IE 6"). |
| wp\_localize\_script() | Adds data before the specified script. |
| wp\_script\_is() | Checks whether the JS file has been registered or is waiting for output. |
| wp\_register\_style() | Registers the CSS file. |
| wp\_enqueue\_style() | Registers and connects the CSS file. |
| wp\_dequeue\_style() | Deletes the CSS file from the output queue. |
| wp\_add\_inline\_style() | Adds inline styles directly to the HTML document. |
| wp\_deregister\_style() | Unregisters the CSS file. |
| wp\_style\_add\_data() | Adds data to styles (e.g., for specific browsers like "IE 6"). |
| wp\_style\_is() | Checks whether the CSS file has been registered or is waiting for output. |

add\_action( 'wp\_enqueue\_scripts', 'add\_my\_scripts' ); // Front

add\_action( 'admin\_enqueue\_scripts', 'add\_my\_scripts' ); // Admin

add\_action( 'login\_enqueue\_scripts', 'add\_my\_scripts' ); // wp-login.php

function add\_my\_scripts(){

if ( ! wp\_script\_is( 'my-script', 'enqueued' ) ) {

// The my-script is not added to the queue

}

if ( ! wp\_style\_is( 'my-style', 'registered' ) ) {

// Styles my-script is not registered

}

wp\_enqueue\_script( 'my-script', 'src', ['deps'], '1.0', 'in\_footer' );

wp\_enqueue\_style( 'my-style', 'src', ['deps'], '1.0', 'all' );

wp\_enqueue\_style( 'theme-style', get\_stylesheet\_uri() ); // theme style.css

wp\_localize\_script( 'my-script', 'myajax', [

'ajaxurl' => admin\_url( 'admin-ajax.php' )

] );

wp\_script\_add\_data( 'my-script', 'conditional', 'lt IE 9' );

wp\_style\_add\_data( 'my-style', 'conditional', 'lt IE 9' )

wp\_add\_inline\_script( 'my-scripts', 'alert("Hello!");' );

wp\_add\_inline\_style( 'my-style', '

.mycolor{ background: #fff;

}

');

wp\_deregister\_script( 'my-script' );

wp\_deregister\_style( 'my-style' );

}

### ****Hooks Functions****

| Function | Description |
| --- | --- |
| add\_action() | Hangs a function on an event. |
| remove\_action() | Deletes a function from the event. |
| did\_action() | Gets a number of how many times the event was performed. |
| do\_action() | Creates an event. |
| do\_action\_ref\_array() | Creates an event; arguments are passed in an array. |
| has\_action() | Checks whether a function is hung on the event. |
| current\_action() | Gets the name of the current event. |
| doing\_action() | Checks if the event is being processed at the moment. |
| remove\_all\_actions() | Deletes all functions attached to the event. |
| add\_filter() | Hangs a function on a filter. |
| remove\_filter() | Deletes a function from the filter. |
| apply\_filters() | Creates a filter. |
| apply\_filters\_ref\_array() | Creates a filter; arguments are passed in an array. |
| has\_filter() | Checks whether the function is hung on the filter. |
| current\_filter() | Gets the name of the current filter. |
| doing\_filter() | Checks if the filter is currently being processed. |
| remove\_all\_filters() | Deletes all functions attached to the filter. |

function my\_filter\_function( $str ){

return 'Hello '. $str;

}

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

// Let's attach a function to the filter

add\_filter( 'my\_filter', 'my\_filter\_function' );

// Call the filter

echo apply\_filters( 'my\_filter', 'John' ); //> Hello John

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

// Create a function for the event

function my\_action\_function( $text ){

echo 'The my\_action event has been triggered just now.';

}

// Let's attach the function to the my\_action event

add\_action( 'my\_action', 'my\_action\_function' );

// Action call

do\_action( 'my\_action' ); //> The my\_action event has been triggered just now.

### ****Localization (Translation)****

| Function | Description |
| --- | --- |
| \_\_() | Gets string translation. |
| \_e() | Outputs a string translation. |
| \_n() | Gets a string translation based on a number. |
| esc\_attr\_\_() | Gets string translation + esc\_attr(). |
| esc\_attr\_e() | Outputs string translation + esc\_attr(). |
| esc\_html\_\_() | Gets string translation + esc\_html(). |
| esc\_html\_e() | Outputs string translation + esc\_html(). |
| \_x() | Gets the string translation for a context. |
| \_ex() | Outputs the string translation for a context. |
| \_nx() | Gets a string translation based on a number and context. |
| date\_i18n() | Gets the translated date (localized date()). |
| determine\_locale() | Gets the locale of the site suitable for the current query. |
| get\_locale() | Gets the locale of the site (e.g., en\_US). |
| get\_user\_locale() | Gets the user's locale. |
| switch\_to\_locale() | Switches the user's locale. |
| is\_locale\_switched() | Checks if switch\_to\_locale() was used. |
| load\_plugin\_textdomain() | Loads .mo file from plugin folder. |
| load\_muplugin\_textdomain() | Loads .mo file from plugin's MU folder. |
| load\_theme\_textdomain() | Loads .mo file from theme folder. |
| load\_child\_theme\_textdomain() | Loads .mo file from child theme folder. |
| load\_textdomain() | Loads specified .mo file from any folder. |
| is\_textdomain\_loaded() | Checks if the .mo file is loaded. |
| unload\_textdomain() | Unloads (removes) the loaded .mo file. |

### ****Conditional Tags (Post Types & Queries)****

| Function | Description |
| --- | --- |
| wp\_doing\_ajax() | Checks if the request is an AJAX request. |
| wp\_doing\_cron() | Checks if it’s a WP Cron request. |
| is\_ssl() | Checks if HTTPS (SSL) is used. |
| is\_front\_page() | Home page. |
| is\_home() | Posts page (or Home page). |
| is\_single() | Single post page of any type except attachment/page. |
| is\_singular() | Page of post of any type. |
| is\_page() | Static page. |
| is\_page\_template() | Checks if a specific template file is used. |
| is\_attachment() | Attachment page. |
| is\_search() | Search results page. |
| is\_archive() | Archive page: category, tag, author, date. |
| is\_category() | Category page. |
| is\_tag() | Tag page. |
| is\_tax() | Custom taxonomy page. |
| is\_post\_type\_archive() | Custom post type archive page. |
| is\_author() | Author posts archive page. |
| is\_date() | Archive page by date. |
| is\_year() | Archive page by year. |
| is\_month() | Archive page by month. |
| is\_day() | Archive page by day. |
| is\_time() | Archive page by hour, minute, second. |
| is\_paged() | Pagination page. |
| is\_404() | “Not Found” page. |
| is\_preview() | Post preview page. |
| is\_feed() | Feed page. |
| is\_admin() | Admin panel. |
| is\_network\_admin() | Network admin panel (Multisite). |
| is\_blog\_admin() | Admin section of a site in Multisite. |
| is\_user\_admin() | User section in Multisite admin. |
| is\_customize\_preview() | Customizer preview page in admin area. |
| is\_robots() | Query to robots.txt file. |
| is\_embed() | Embedded post page. |
| is\_comment\_feed() | Comments feed page. |
| is\_trackback() | Trackback/ping page. |

### Conditional tags (others)

if( is\_user\_logged\_in() ){

// user is authorized

}

| Function | Description |
| --- | --- |
| is\_user\_logged\_in() | Checks if the user is logged in. |
| have\_comments() | Checks if there are comments to display on the page. |
| comments\_open() | Checks if comments are open. |
| has\_category() | Checks if the post is in at least one category. |
| has\_tag() | Checks if the post is in at least one tag. |
| has\_term() | Checks if the post is in at least one taxonomy term. |
| has\_excerpt() | Checks if the post has an excerpt (quote or short description). |
| is\_nav\_menu() | Checks if there is a menu by ID, slug, or name. |
| has\_nav\_menu() | Checks if a registered menu area has an attached menu. |
| has\_shortcode() | Checks if content contains the specified shortcode. |
| shortcode\_exists() | Checks if the specified shortcode is registered. |
| in\_category() | Checks if the post is in a category. |
| in\_the\_loop() | Checks if we are inside a WordPress Loop. |
| is\_main\_query() | Checks if we are in the main WordPress Loop. |
| is\_active\_sidebar() | Checks if there is at least one widget in the widget area. |
| is\_child\_theme() | Checks if a child theme is being used. |
| is\_dynamic\_sidebar() | Checks if theme sidebars are enabled and have at least one widget. |
| is\_local\_attachment() | Checks if the given URL is an attachment page. |
| is\_multisite() | Checks if multisite mode is turned on. |
| is\_new\_day() | Checks if the current date differs from the previous (in the loop). |
| is\_post\_type\_hierarchical() | Checks if the post type is hierarchical (tree-like). |
| is\_taxonomy\_hierarchical() | Checks if the taxonomy is hierarchical (tree-like). |
| is\_sticky() | Checks if the post is sticky (shown on the front page). |
| pings\_open() | Checks if the post is allowed to receive pings. |
| post\_exists() | Checks if a post exists with the specified title (post\_title). |
| taxonomy\_exists() | Checks if the specified taxonomy exists. |
| post\_password\_required() | Checks if the post is password protected and if the password is correct. |
| term\_exists() | Checks if the taxonomy term exists (returns the term ID). |
| cat\_is\_ancestor\_of() | Checks if a category is a child of another category (all nesting levels). |
| term\_is\_ancestor\_of() | Checks if a term is a child of another term (all nesting levels). |
| wp\_attachment\_is() | Checks if the attachment is an image, audio, or video. |
| wp\_attachment\_is\_image() | Checks if the attachment (post) is an image. |
| is\_header\_video\_active() | Checks if the header video should be shown on the page. |
| has\_custom\_header() | Checks if a picture/video is set for the theme header. |
| wp\_is\_mobile() | Checks if the site is viewed on a mobile device. |
| wp\_is\_post\_autosave() | Checks if the post is an auto-save. |
| wp\_is\_post\_revision() | Checks if the post is a revision. |

### ****Template Tags****

| Function | Description |
| --- | --- |
| home\_url() | Gets the URL of the homepage. |
| site\_url() | Gets the URL of the admin panel. |
| wp\_get\_document\_title() | Gets the page title for <title>. |
| the\_archive\_title() | Outputs the title of the archive page (tag, category, date). |
| single\_term\_title() | Outputs/gets the title of the term page. |
| single\_post\_title() | Outputs/gets the title of a post page. |
| single\_cat\_title() | Outputs/gets title of a category/tag page. |
| body\_class() | Outputs CSS classes for the <body> tag. |
| wp\_body\_open() | Triggers the wp\_body\_open hook (use after \<body>). |
| wp\_head() | Triggers the wp\_head hook (use in header.php). |
| wp\_footer() | Triggers the wp\_footer hook (use in footer.php). |
| wp\_list\_categories() | Outputs a list of categories as links. |
| wp\_dropdown\_categories() | Outputs a dropdown list of categories/terms. |
| wp\_list\_comments() | Outputs/gets post comments. |
| comment\_form() | Outputs the comment form. |
| wp\_tag\_cloud() | Outputs/gets the tag cloud. |
| register\_sidebar() | Registers a widget panel. |
| register\_sidebars() | Registers multiple widget panels. |
| wp\_nav\_menu() | Outputs a custom menu created in admin panel. |
| register\_nav\_menu() | Registers a single menu location (area). |
| register\_nav\_menus() | Registers multiple menu locations (areas). |
| wp\_get\_attachment\_image() | Gets an image <img> tag. |
| wp\_get\_attachment\_image\_src() | Gets image data: URL, width, height. |
| wp\_get\_attachment\_image\_url() | Gets image URL by its ID. |
| category\_description() | Gets category description. |
| term\_description() | Gets term description. |
| get\_the\_term\_list() | Outputs a list of post terms as links. |
| get\_avatar() | Gets user avatar image (\<img> tag). |
| next\_post\_link() | Displays a link to the next most recent post. |
| previous\_post\_link() | Displays a link to the previous most recent post. |
| get\_post\_type\_archive\_link() | Gets the URL for the post type archive page. |
| wp\_link\_pages() | Outputs pagination for multi-page posts (<!--nextpage-->). |
| the\_post\_navigation() | Outputs links to next/previous posts as HTML block. |
| wp\_get\_archives() | Outputs links to date archive pages: days, months, years. |
| wp\_login\_form() | Outputs login form HTML code. |
| edit\_tag\_link() | Outputs a link to edit the current tag. |
| edit\_term\_link() | Outputs a link to edit the current term. |

### ****Formatting Functions****

| Function | Description |
| --- | --- |
| absint() | Converts a value to a non-negative integer. |
| antispambot() | Converts email characters to HTML entities. |
| force\_balance\_tags() | Fixes unclosed or incorrect HTML tags. |
| links\_add\_target() | Adds a target attribute to <a> tags. |
| make\_clickable() | Converts plain URLs into HTML links. |
| normalize\_whitespace() | Replaces line breaks with \n, removes extra spaces. |
| number\_format\_i18n() | Formats numbers according to localization. |
| size\_format() | Converts bytes to readable sizes: 500 B, 63 KB, 9 MB, etc. |
| set\_url\_scheme() | Fixes URL protocol; "relative" removes domain. |
| wp\_rel\_nofollow() | Adds rel="nofollow" to <a> links (skips internal links). |
| trailingslashit() | Adds a slash (/) at the end of a string. |
| untrailingslashit() | Removes trailing slash from a string. |
| user\_trailingslashit() | Adds/removes slash based on WP permalink settings. |
| wp\_trim\_words() | Trims text to a specified number of words. |
| wpautop() | Converts double newlines to \<p> and single to \<br>. |
| wptexturize() | Converts characters like (tm) to ™, etc. |
| zeroise() | Adds leading zeros if needed (10 → 0010). |

### ****Escaping Functions (Output Safety)****

| Function | Description |
| --- | --- |
| esc\_attr() | Escapes string for use in HTML tag attributes. |
| esc\_html() | Escapes string for safe display on screen. |
| esc\_url() | Escapes string for use in URLs (src=, href=, etc.). |
| esc\_textarea() | Escapes string for <textarea> values. |
| wp\_strip\_all\_tags() | Removes all HTML tags. |
| wp\_kses() | Filters HTML content, leaving allowed tags. |
| esc\_js() | Prepares string for safe use in JavaScript. |
| esc\_sql() | Escapes string for use in SQL queries. |

### ****Sanitization Functions (Input Safety)****

| Function | Description |
| --- | --- |
| sanitize\_text\_field() | Cleans string, removes HTML, extra spaces. |
| sanitize\_textarea\_field() | Cleans string from textarea before saving to DB. |
| sanitize\_key() | Cleans string for use as a key or ID. |
| sanitize\_url() | Cleans string for redirects or DB storage. |
| sanitize\_html\_class() | Cleans string for HTML class attribute. |
| sanitize\_email() | Cleans string to valid email characters. |
| sanitize\_file\_name() | Cleans file name, replaces spaces with \_, removes invalid chars. |
| sanitize\_title\_with\_dashes() | Cleans title, replaces spaces with -. |
| sanitize\_mime\_type() | Removes all chars except allowed MIME type chars (-+\*.a-zA-Z0-9/). |
