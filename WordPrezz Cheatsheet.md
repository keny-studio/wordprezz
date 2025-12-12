# $${\color{red}UNDER \ CONSTRUCTION}$$

# WordPress Cheatsheet

---

## 1. Template Functions

| Function | Description |
|----------|-------------|
| `<?php get_header(); ?>` | Includes `header.php`. |
| `<?php get_template_part('file'); ?>` | Includes `file.php`. |
| `<?php get_search_form(); ?>` | Includes search form (`searchform.php`). |
| `<?php comments_template(); ?>` | Includes comments form (`comments.php`). |
| `<?php get_sidebar(); ?>` | Includes `sidebar.php`. |
| `<?php get_footer(); ?>` | Includes `footer.php`. |
| `get_template_directory()` | Path to parent theme (no trailing slash). |
| `get_stylesheet_directory()` | Path to parent/child style.css (no trailing slash). |
| `get_parent_theme_file_path()` | File path of parent theme. |
| `get_theme_file_path()` | File path of parent/child theme. |
| `load_template()` | Includes file (`require_once`). |
| `locate_template()` | Finds/includes parent/child theme file. |
| `get_template_directory_uri()` | URL of parent theme. |
| `get_stylesheet_directory_uri()` | URL of child theme if exists. |
| `get_theme_root_uri()` | URL of theme's directory. |
| `get_stylesheet_uri()` | URL of theme's `style.css`. |
| `get_theme_file_uri()` | URL of parent/child theme file. |
| `get_parent_theme_file_uri()` | URL of parent theme file. |

---

## 2. Theme Files (Hierarchy) `/themes/THEME/`

| File | Description |
|------|-------------|
| `style.css` | Theme styles file (required). |
| `index.php` | Fallback template file (required). |
| `front-page.php` | Home page template. |
| `home.php` | Posts page template (or Home page). |
| `functions.php` | PHP functions file. |
| `404.php` | "Not found" page. |
| `comments.php` | Comments template. |
| `header.php` | Site header template. |
| `searchform.php` | Search form template. |
| `sidebar.php` | Sidebar template. |
| `footer.php` | Footer template. |
| `single.php` | Single post template (`post_type=post`). |
| `single-POST_TYPE.php` | Single post template for custom post type. |
| `single-POST_TYPE-POST_NAME.php` | Single post template for custom post type and name. |
| `singular.php` | Single post template for any post type. |
| `page.php` | Page template (`post_type=page`). |
| `page-POST_NAME.php` | Page template for a specific slug. |
| `page-ID.php` | Page template for a specific ID. |
| `attachment.php` | Any attachment page. |
| `image.php` | Image attachment page. |
| `archive.php` | Generic archive page. |
| `archive-POST_TYPE.php` | Archive for custom post type. |
| `search.php` | Search result page. |
| `category.php` | Category archive page. |
| `category-SLUG.php` | Category archive by slug. |
| `category-ID.php` | Category archive by ID. |
| `tag.php` | Tag archive page. |
| `tag-SLUG.php` | Tag archive by slug. |
| `tag-ID.php` | Tag archive by ID. |
| `taxonomy.php` | Custom taxonomy page. |
| `taxonomy-TAXONOMY.php` | Taxonomy archive for any term. |
| `taxonomy-TAXONOMY-SLUG.php` | Taxonomy archive for a specific slug. |
| `author.php` | Author posts archive page. |

---

## 3. Site Information (`bloginfo`)

| Function | Description |
|----------|-------------|
| `bloginfo()` | Displays information about the site. |
| `get_bloginfo()` | Gets information about the site. |
| `bloginfo('name')` | Site name. |
| `bloginfo('description')` | Site tagline. |
| `bloginfo('template_url')` | Theme URL (`get_template_directory()`). |
| `bloginfo('template_directory')` | Same as `template_url`. |
| `bloginfo('stylesheet_directory')` | Child theme URL (`get_stylesheet_directory_uri()`). |
| `bloginfo('stylesheet_url')` | Style.css URL (`get_stylesheet_uri()`). |
| `bloginfo('charset')` | Site encoding (UTF-8). |
| `bloginfo('html_type')` | Content type (text/html). |
| `bloginfo('language')` | Site language/locale. |
| `bloginfo('version')` | WordPress version. |
| `bloginfo('rss2_url')` | Feed URL (/feed). |
| `bloginfo('comments_rss2_url')` | Comments feed URL. |
| `bloginfo('admin_email')` | Admin email. |
| `bloginfo('pingback_url')` | Pingback URL. |
| `bloginfo('rdf_url')` | RDF feed URL. |
| `bloginfo('rss_url')` | RSS 0.92 feed URL. |
| `bloginfo('atom_url')` | Atom feed URL. |
| `bloginfo('url')` | Home URL. |
| `bloginfo('wpurl')` | Admin panel URL. |

---

## 4. Comment Loop Functions

| Function | Description |
|----------|-------------|
| `comment_ID()` | Displays the ID of the current comment. |
| `comments_popup_link()` | Displays a link to the comment popup. |
| `comment_text()` | Displays the text of the comment. |
| `comment_author()` | Displays the comment author name. |
| `comments_link()` | Displays a URL to post comment form. |
| `comment_reply_link()` | Displays a reply link for comments. |
| `comment_time()` | Displays comment publishing time. |
| `comment_author_link()` | Displays comment author as a link. |
| `comment_author_url()` | Displays comment author URL. |
| `comment_author_url_link()` | Displays comment author link (A tag). |
| `comment_author_email_link()` | Displays comment author email as `mailto:` link. |
| `edit_comment_link()` | Displays edit comment link. |

---

## 5. The Loop

| Function | Description |
|----------|-------------|
| `in_the_loop()` | Checks if WP loop is active. |
| `have_posts()` | Checks if posts exist for the loop. |
| `the_post()` | Sets the next post and `$post` global. |
| `setup_postdata()` | Sets global `$post`. |
| `the_ID()` | Displays current post ID. |
| `the_title()` | Displays current post title. |
| `the_title_attribute()` | Displays post title for HTML attribute. |
| `the_content()` | Displays post content. |
| `the_excerpt()` | Displays post excerpt. |
| `the_excerpt_rss()` | Displays excerpt for RSS. |
| `get_permalink()` | Gets post URL. |
| `the_permalink()` | Displays post URL. |
| `comments_number()` | Displays number of comments. |
| `edit_post_link()` | Displays edit post link. |
| `the_date()` | Displays post creation date. |
| `get_the_date()` | Gets post creation date. |
| `the_time()` | Displays post time. |
| `get_post_time()` | Gets post time. |
| `the_modified_date()` | Displays modified date. |
| `the_post_thumbnail()` | Displays post thumbnail image HTML. |
| `get_post_thumbnail_id()` | Gets post thumbnail ID. |
| `has_post_thumbnail()` | Checks if post has a thumbnail. |
| `the_post_thumbnail_url()` | Displays post thumbnail URL. |
| `the_attachment_link()` | Displays attachment link. |
| `get_attachment_link()` | Gets URL to attachment page. |
| `wp_get_attachment_link()` | Gets attachment link (A tag). |
| `the_tags()` | Displays post tags as links. |
| `the_category()` | Displays post categories as links. |
| `the_taxonomies()` | Displays post terms as links. |
| `in_category()` | Checks if post belongs to category. |
| `sticky_class()` | Displays `sticky` class if post is sticky. |
| `is_sticky()` | Checks if post is sticky. |
| `the_meta()` | Displays post meta-fields as `<li>`. |
| `get_post_format()` | Gets post format (`quote`, `status`, `video`, etc.). |
| `the_author()` | Displays post author name. |
| `get_the_author()` | Gets post author display name. |
| `the_author_link()` | Displays author link (A tag). |
| `get_the_author_link()` | Gets author link (A tag). |
| `the_author_posts()` | Displays total posts by author. |
| `the_author_posts_link()` | Displays link to author archive page. |
| `the_author_meta()` | Displays author meta-field. |
| `get_the_author_meta()` | Gets author meta-field. |
| `the_modified_author()` | Displays last modified author name. |

---

## 6. WP-CLI Commands

### Core

```bash
# Download WordPress
wp core download --locale=ru_RU

# Generate wp-config.php
wp core config --dbname=NAME --dbuser=USER --dbpass=PASS --dbprefix=wp_

# Create DB
wp db create

# Install WP
wp core install --url=example.com --title=Example --admin_user=supervisor --admin_email=info@example.com --admin_password=strongpassword
Posts
bash
Skopiuj kod
# List posts
wp post list

# Edit post
wp post edit 1

# Update post
wp post update 1 --post_title="Your New title..."

# Create post
wp post create --post_status=publish --post_title="Second Post" --edit
Post Meta
bash
Skopiuj kod
# List post meta
wp post meta list 18

# Get post meta
wp post meta get 18 meta_name

# Delete post meta
wp post meta delete 18 meta_name
Database
bash
Skopiuj kod
# Export DB dump
wp db export - --add-drop-table --default-character-set=utf8mb4 | gzip > ./db-dump-$(date +%Y-%m-%d-%H%M%S).sql.gz

# Import DB
wp db import db_backup-2022-01-20.sql

# DB CLI
wp db cli

# Run SQL query
wp db query "SELECT user_login, ID FROM wp_users;"

# Optimize DB
wp db optimize
Updates
bash
Skopiuj kod
# Update WordPress
wp core update

# Update all plugins
wp plugin update --all
Themes & Plugins
bash
Skopiuj kod
# List plugins
wp plugin list

# Search plugin
wp plugin search yoast

# Install plugin
wp plugin install yoast

# List themes
wp theme list

# Install theme
wp theme install twentyone

# Activate theme
wp theme activate twentyone
7. Plugin Functions
Function	Description
register_activation_hook()	Registers function to activate plugin.
register_deactivation_hook()	Registers function to deactivate plugin.
register_uninstall_hook()	Registers function for plugin uninstall.
plugins_url()	Gets URL of plugins folder.
plugin_basename()	Path to plugin file.
plugin_dir_path()	Gets path to plugin folder.
plugin_dir_url()	Gets URL of plugin folder.
get_plugins()	Gets all plugins data.
get_plugin_data()	Gets plugin data from headers.
activate_plugins()	Activates plugins.
deactivate_plugins()	Deactivates plugins.
is_plugin_active()	Checks if plugin is active.

uninstall.php example
php
Skopiuj kod
<?php
if( ! defined('WP_UNINSTALL_PLUGIN') ) exit;
delete_option('plug_option');
8. Script & Style Functions
Function	Description
wp_register_script()	Registers a JS file.
wp_enqueue_script()	Registers and enqueues JS file.
wp_dequeue_script()	Removes script from queue.
wp_add_inline_script()	Adds inline JS to registered script.
wp_deregister_script()	Unregisters JS file.
wp_script_add_data()	Adds data to script (e.g., IE only).
wp_localize_script()	Adds data for a script.
wp_script_is()	Checks if script is registered/enqueued.
wp_register_style()	Registers CSS file.
wp_enqueue_style()	Registers and enqueues CSS file.
wp_dequeue_style()	Removes CSS file from queue.
wp_add_inline_style()	Adds inline CSS.
wp_deregister_style()	Unregisters CSS file.
wp_style_add_data()	Adds data to style (e.g., IE only).
wp_style_is()	Checks if style is registered/enqueued.

9. Hooks Functions
Function	Description
add_action()	Adds function to an action hook.
remove_action()	Removes function from action hook.
did_action()	Returns number of times an action was triggered.
do_action()	Triggers an action hook.
do_action_ref_array()	Triggers action with arguments array.
has_action()	Checks if function is hooked.
current_action()	Returns current action name.
doing_action()	Checks if action is running.
remove_all_actions()	Removes all functions from hook.
add_filter()	Adds function to a filter hook.
remove_filter()	Removes function from filter hook.
apply_filters()	Applies filter to value.
apply_filters_ref_array()	Applies filter with arguments array.
has_filter()	Checks if function is hooked to filter.
current_filter()	Returns current filter name.
doing_filter()	Checks if filter is running.
remove_all_filters()	Removes all functions from filter.

10. Localization Functions
Function	Description
__()	Gets string translation.
_e()	Echoes string translation.
_n()	Gets translation based on number.
esc_attr__()	Escaped string translation for attributes.
esc_attr_e()	Echo escaped string for attributes.
esc_html__()	Escaped string translation for HTML.
esc_html_e()	Echo escaped string for HTML.
_x()	Gets translation with context.
_ex()	Echo translation with context.
_nx()	Gets translation based on number and context.
date_i18n()	Returns localized date.
determine_locale()	Gets locale for current query.
get_locale()	Returns site locale.
get_user_locale()	Returns user locale.
switch_to_locale()	Switches user locale.
is_locale_switched()	Checks if locale was switched.
load_plugin_textdomain()	Loads plugin .mo file.
load_muplugin_textdomain()	Loads MU plugin .mo file.
load_theme_textdomain()	Loads theme .mo file.
load_child_theme_textdomain()	Loads child theme .mo file.
load_textdomain()	Loads specified .mo file.
is_textdomain_loaded()	Checks if .mo file is loaded.
unload_textdomain()	Unloads .mo file.

11. Conditional & Utility Functions
Function	Description
is_user_logged_in()	Checks if user is logged in.
have_comments()	Checks if there are comments.
comments_open()	Checks if comments are open.
has_category()	Checks if post is in at least one category.
has_tag()	Checks if post is in at least one tag.
has_term()	Checks if post is in at least one taxonomy term.
has_excerpt()	Checks if post has an excerpt.
is_nav_menu()	Checks if menu exists by ID, slug, or name.
has_nav_menu()	Checks if menu area has menu attached.
has_shortcode()	Checks if content contains a shortcode.
shortcode_exists()	Checks if shortcode is registered.
in_category()	Checks if post is in a category.
in_the_loop()	Checks if inside WP Loop.
is_main_query()	Checks if in main WP Loop.
is_active_sidebar()	Checks if widget exists in sidebar.
is_child_theme()	Checks if child theme is active.
is_dynamic_sidebar()	Checks if sidebar enabled & has widgets.
is_local_attachment()	Checks if URL is attachment page.
is_multisite()	Checks if multisite enabled.
is_new_day()	Checks if current date differs from previous (in loop).
is_post_type_hierarchical()	Checks if post type is hierarchical.
is_taxonomy_hierarchical()	Checks if taxonomy is hierarchical.
is_sticky()	Checks if post is sticky.
pings_open()	Checks if post can receive pings.
post_exists()	Checks if post exists by title.
taxonomy_exists()	Checks if taxonomy exists.
post_password_required()	Checks if post is password protected.
term_exists()	Checks if term exists (returns ID).
cat_is_ancestor_of()	Checks if category is child of another.
term_is_ancestor_of()	Checks if term is child of another.
wp_attachment_is()	Checks if attachment is image/audio/video.
wp_attachment_is_image()	Checks if attachment is an image.
is_header_video_active()	Checks if header video is active.
has_custom_header()	Checks if header image/video is set.
wp_is_mobile()	Checks if viewed on mobile device.
wp_is_post_autosave()	Checks if post is auto-save.
wp_is_post_revision()	
