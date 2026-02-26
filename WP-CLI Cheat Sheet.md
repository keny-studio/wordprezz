## $${\color{red}WP-CLI \ Cheat \ Sheet}$$

WP-CLI is a command-line interface for managing WordPress installations.

---

### 📦 Installation & Info

```bash
wp --info                 # Show WP-CLI + environment info
wp cli version            # Show WP-CLI version
wp cli update             # Update WP-CLI
```

---

### ⚙️ Core Management

```bash
wp core download                          # Download WordPress
wp core config --dbname=db --dbuser=user --dbpass=pass
wp core install --url=example.com --title="Site" --admin_user=admin --admin_password=pass --admin_email=email@example.com

wp core version                           # WP version
wp core update                            # Update core
wp core update-db                         # Update DB
wp core verify-checksums                  # Verify core integrity
```

---

### 🔌 Plugin Management

```bash
wp plugin list
wp plugin install akismet --activate
wp plugin activate plugin-name
wp plugin deactivate plugin-name
wp plugin delete plugin-name
wp plugin update --all
wp plugin status
```

Search plugins:

```bash
wp plugin search seo --per-page=5
```

---

### 🎨 Theme Management

```bash
wp theme list
wp theme install twentytwentyfour --activate
wp theme activate theme-name
wp theme delete theme-name
wp theme update --all
wp theme status
```

---

### 👤 User Management

```bash
wp user list
wp user create john john@example.com --role=editor --user_pass=pass
wp user update 2 --role=administrator
wp user delete 5 --reassign=1
wp user reset-password admin
```

---

### 📝 Posts & Content

```bash
wp post list
wp post create --post_type=post --post_title="Hello" --post_status=publish
wp post update 123 --post_status=draft
wp post delete 123 --force
```

Custom Post Types:

```bash
wp post list --post_type=product
```

---

### 🗄️ Database

```bash
wp db create
wp db drop
wp db reset
wp db export backup.sql
wp db import backup.sql
wp db optimize
wp db tables
wp db size
```

Search & replace:

```bash
wp search-replace 'http://old.com' 'https://new.com' --all-tables
```

---

### 🌍 URL & Migration

```bash
wp option get siteurl
wp option update home https://example.com
wp rewrite flush
```

Dry run migration:

```bash
wp search-replace 'old.com' 'new.com' --dry-run
```

---

### 🔁 Cron & Cache

```bash
wp cron event list
wp cron event run --due-now
wp cache flush
```

---

### 📦 Media

```bash
wp media list
wp media regenerate
wp media import image.jpg --post_id=123
```

---

### 🛠️ Options & Transients

```bash
wp option list
wp option get blogname
wp option update blogdescription "New description"

wp transient list
wp transient delete --all
```

---

### 🧩 Multisite

```bash
wp site list
wp site create --slug=subsite
wp network meta list
```

---

### 🔐 Capabilities & Roles

```bash
wp role list
wp role create seo_manager "SEO Manager"
wp cap add editor manage_options
```

---

### 🧪 Eval & Debugging

```bash
wp eval 'echo get_bloginfo("name");'
wp eval-file script.php
wp shell
```

Enable debugging:

```bash
wp config set WP_DEBUG true --raw
```

---

### 🚀 Advanced Developer Commands

Run as specific user:

```bash
wp post list --user=1
```

Run on remote server via SSH:

```bash
wp --ssh=user@server.com plugin list
```

Run on specific path:

```bash
wp --path=/var/www/html plugin list
```

Run on specific URL (multisite):

```bash
wp --url=sub.example.com plugin list
```

---

### 📚 Useful Flags

```bash
--allow-root
--skip-plugins
--skip-themes
--quiet
--debug
--format=table|json|csv|ids
```

Example JSON output:

```bash
wp plugin list --format=json
```

