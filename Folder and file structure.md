## ${\color{red}WordPress \ Folder \ and \ File \ Structure}$

<br>

|${\color{red}Folder \ Structure}$ | | |
|-----|------|-------------|
| | | |
| Path | Type | Description |
| | | |
| `/wp-admin/` | Folder | WordPress admin dashboard files |
| `/wp-includes/` | Folder | Core WordPress libraries, APIs, and functions |
| `/wp-content/` | Folder | Custom and user-generated content |
| `/wp-content/themes/` | Folder | Installed WordPress themes |
| `/wp-content/themes/parent-theme/` | Theme | Parent theme (e.g. Twenty Twenty-Four) |
| `/wp-content/themes/parent-theme/style.css` | File | Parent theme main stylesheet |
| `/wp-content/themes/parent-theme/functions.php` | File | Parent theme functions |
| `/wp-content/themes/parent-theme/template-parts/` | Folder | Parent theme reusable templates |
| `/wp-content/themes/child-theme/` | Theme | Child theme |
| `/wp-content/themes/child-theme/style.css` | Required | Child theme declaration & CSS |
| `/wp-content/themes/child-theme/functions.php` | Required | Enqueues parent & child styles |
| `/wp-content/themes/child-theme/index.php` | Recommended | Prevents fallback issues |
| `/wp-content/themes/child-theme/screenshot.png` | Optional | Theme preview image |
| `/wp-content/themes/child-theme/header.php` | Optional | Overrides parent header |
| `/wp-content/themes/child-theme/footer.php` | Optional | Overrides parent footer |
| `/wp-content/themes/child-theme/single.php` | Optional | Overrides parent single post |
| `/wp-content/themes/child-theme/template-parts/` | Folder | Child overrides of template parts |
| `/wp-content/plugins/` | Folder | Installed plugins |
| `/wp-content/plugins/plugin-name/` | Plugin | Plugin directory |
| `/wp-content/mu-plugins/` | Folder | Must-Use plugins (auto-loaded) |
| `/wp-content/uploads/` | Folder | Media uploads (year/month) |
| `/wp-content/languages/` | Folder | Translation files (.mo/.po) |
| `/wp-config.php` | File | WordPress configuration |
| `/.htaccess` | File | Server rules (Apache) |
| `/index.php` | File | WordPress front controller |
| `/xmlrpc.php` | File | Remote API access |

<br>

|${\color{red}File \ Structure}$ | | |
|----------|----------|---------------------------|
| | | |
| **Item** | **Type** | **Purpose / Description** |
| | | |
| `.htaccess` | Static config file | Apache web server configuration for permalinks and redirects. |
| `license.txt` | Static file | Contains the WordPress GNU GPLv2 license details. |
| `readme.html` | Static file | Documentation about installing/updating WordPress, system requirements, and online resources. |
| `index.php` | Core PHP file | Entry point for WordPress, kicks off loading of the application.  |
| `wp-blog-header.php` | Core PHP file | Bootstraps WordPress and loads the environment. |
| `wp-load.php` | Core PHP file | Loads the WordPress environment and connects all files. |
| `wp-config.php` | Config file | Main configuration (database credentials, keys, custom settings).  |
| `wp-settings.php` | Core PHP file | Loads core WordPress functionality during bootstrap. |
| `wp-activate.php` | Specific action file | Handles activation requests (especially Multisite).  |
| `wp-comments-post.php` | Specific action file | Processes submitted comments. |
| `wp-cron.php` | Cron tasks runner | Handles scheduled tasks like publishing or maintenance jobs. |
| `wp-links-opml.php` | Legacy OPML generator | Generates XML link lists (rarely used).  |
| `wp-login.php` | Login handler | Displays and processes the login form. |
| `wp-mail.php` | Mail publishing handler | Handles posts via email (if enabled). |
| `wp-signup.php` | Signup handler | Handles site/user signup (Multisite). |
| `wp-trackback.php` | Trackback processor | Handles incoming trackbacks.  |
| `xmlrpc.php` | XML-RPC API | Handles remote XML-RPC requests (mobile apps, external systems).|

