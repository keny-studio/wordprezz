## $${\color{red}wp-config.php \ Cheat \ Sheet}$$

`wp-config.php` is the core configuration file of WordPress.
It controls database connection, security keys, debugging, environment settings, and advanced behavior.

---

### 📍 1. File Location

```
/public_html/
 ├── wp-admin/
 ├── wp-content/
 ├── wp-includes/
 ├── wp-config.php  ← here
```

You can move it one level above public root for security.

---

### 🗄️ 2. Database Configuration

```php
define('DB_NAME', 'database_name');
define('DB_USER', 'database_user');
define('DB_PASSWORD', 'database_password');
define('DB_HOST', 'localhost'); // or 127.0.0.1
define('DB_CHARSET', 'utf8mb4');
define('DB_COLLATE', '');
```

### Notes:

* `DB_HOST` may include port: `localhost:3306`
* Use `utf8mb4` for full emoji support
* Never commit real credentials to Git

---

### 🔐 3. Authentication Unique Keys & Salts

```php
define('AUTH_KEY',         '...');
define('SECURE_AUTH_KEY',  '...');
define('LOGGED_IN_KEY',    '...');
define('NONCE_KEY',        '...');
define('AUTH_SALT',        '...');
define('SECURE_AUTH_SALT', '...');
define('LOGGED_IN_SALT',   '...');
define('NONCE_SALT',       '...');
```

Generate fresh keys from:
[https://api.wordpress.org/secret-key/1.1/salt/](https://api.wordpress.org/secret-key/1.1/salt/)

✔ Regenerate to force logout all users.

---

### 🧩 4. Table Prefix

```php
$table_prefix = 'wp_';
```

Change for security or multisite separation.

Example:

```php
$table_prefix = 'psproj_';
```

---

### 🐛 5. Debug Mode (Development)

```php
define('WP_DEBUG', true);
define('WP_DEBUG_LOG', true);
define('WP_DEBUG_DISPLAY', false);
define('SCRIPT_DEBUG', true);
define('SAVEQUERIES', true);
```

### Debug Best Practice (Safe Setup)

```php
if (!defined('WP_DEBUG')) {
    define('WP_DEBUG', true);
    define('WP_DEBUG_LOG', true);
    define('WP_DEBUG_DISPLAY', false);
}
```

Debug log file:

```
/wp-content/debug.log
```

🚫 Never enable debug on production.

---

### 🌍 6. Environment Type (WP 5.5+)

```php
define('WP_ENVIRONMENT_TYPE', 'development');
```

Possible values:

* `production`
* `staging`
* `development`
* `local`

---

### 🔒 7. Security Hardening

### Disable File Editing in Admin

```php
define('DISALLOW_FILE_EDIT', true);
```

### Disable Plugin/Theme Installation

```php
define('DISALLOW_FILE_MODS', true);
```

### Force SSL Admin

```php
define('FORCE_SSL_ADMIN', true);
```

---

### 🚀 8. Performance Tweaks

### Increase Memory Limit

```php
define('WP_MEMORY_LIMIT', '256M');
define('WP_MAX_MEMORY_LIMIT', '512M');
```

### Enable Cache (for caching plugins)

```php
define('WP_CACHE', true);
```

---

### 🔄 9. Auto Updates Control

### Disable All Updates

```php
define('AUTOMATIC_UPDATER_DISABLED', true);
```

### Disable Core Updates

```php
define('WP_AUTO_UPDATE_CORE', false);
```

### Disable Plugin Updates

```php
add_filter('auto_update_plugin', '__return_false');
```

---

### 🌐 10. Site URL Override

Useful for migrations or staging:

```php
define('WP_HOME', 'https://example.com');
define('WP_SITEURL', 'https://example.com');
```

---

### 🧱 11. Multisite Activation

```php
define('WP_ALLOW_MULTISITE', true);
```

After setup, additional config is generated.

---

### 🗃️ 12. Custom Content Directory

```php
define('WP_CONTENT_DIR', dirname(__FILE__) . '/content');
define('WP_CONTENT_URL', 'https://example.com/content');
```

---

### 🛠️ 13. Cron Control

Disable built-in cron (use real server cron instead):

```php
define('DISABLE_WP_CRON', true);
```

Then create server cron:

```
*/5 * * * * php /path/to/wp-cron.php
```

---

### 🧪 14. Post Revisions Control

```php
define('WP_POST_REVISIONS', 5); // limit revisions
```

Or disable:

```php
define('WP_POST_REVISIONS', false);
```

---

### 🧹 15. Trash Control

```php
define('EMPTY_TRASH_DAYS', 7);
```

Disable trash:

```php
define('EMPTY_TRASH_DAYS', 0);
```

---

### 🧾 16. Advanced: Database Repair

```php
define('WP_ALLOW_REPAIR', true);
```

Visit:

```
/wp-admin/maint/repair.php
```

⚠ Remove after use.

---

### 🧩 17. Disable Theme/Plugin Editor

Already mentioned but critical:

```php
define('DISALLOW_FILE_EDIT', true);
```

---

### 📌 18. Order Matters

Keep this line at the bottom:

```php
/* That's all, stop editing! Happy publishing. */
require_once ABSPATH . 'wp-settings.php';
```

Anything custom goes above it.

---

### 🛡️ Production Best Practice Block

```php
define('WP_DEBUG', false);
define('DISALLOW_FILE_EDIT', true);
define('FORCE_SSL_ADMIN', true);
define('WP_ENVIRONMENT_TYPE', 'production');
```

---

### 🔥 Developer Tips

* Never commit real `wp-config.php`
* Use `.env` + require pattern for modern workflow
* Store secrets outside web root
* Use different configs per environment
* Keep salts unique per environment

