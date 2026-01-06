## $${\color{red}WordPress \ Database \ Cheat \ Sheet}$$


---

## 1️⃣ Core WordPress Database Tables

Default prefix: `wp_` (can be different!)

### 🔹 Content & Structure

| Table                   | Purpose                                      |
| ----------------------- | -------------------------------------------- |
| `wp_posts`              | Posts, pages, attachments, CPTs, revisions   |
| `wp_postmeta`           | Metadata for posts (custom fields)           |
| `wp_terms`              | Categories, tags, custom terms               |
| `wp_term_taxonomy`      | Taxonomy definitions (category, tag, custom) |
| `wp_term_relationships` | Links posts ↔ terms                          |

---

### 🔹 Users

| Table         | Purpose                            |
| ------------- | ---------------------------------- |
| `wp_users`    | User accounts                      |
| `wp_usermeta` | User metadata, roles, capabilities |

---

### 🔹 Comments

| Table            | Purpose          |
| ---------------- | ---------------- |
| `wp_comments`    | Comments         |
| `wp_commentmeta` | Comment metadata |

---

### 🔹 Settings & System

| Table        | Purpose                        |
| ------------ | ------------------------------ |
| `wp_options` | Site-wide settings, transients |
| `wp_links`   | Blogroll (legacy)              |

---

## 2️⃣ `wp_posts` – Key Columns

| Column         | Meaning                          |
| -------------- | -------------------------------- |
| `ID`           | Primary key                      |
| `post_type`    | `post`, `page`, `product`, CPT   |
| `post_status`  | `publish`, `draft`, `private`    |
| `post_title`   | Title                            |
| `post_content` | Main content                     |
| `post_author`  | User ID                          |
| `post_date`    | Created date                     |
| `post_parent`  | Attachments / hierarchical posts |

👉 **WooCommerce products = `post_type = 'product'`**

---

## 3️⃣ Metadata Pattern (`*_meta` tables)

Used in:

* `wp_postmeta`
* `wp_usermeta`
* `wp_commentmeta`

| Column       | Meaning               |
| ------------ | --------------------- |
| `meta_id`    | Primary key           |
| `*_id`       | Parent ID             |
| `meta_key`   | Key name              |
| `meta_value` | Stored value (string) |

⚠️ **No schema enforcement** – values are serialized strings often.

---

## 4️⃣ Taxonomy Structure (IMPORTANT)

Relationships:

```
wp_posts
  ↕
wp_term_relationships
  ↕
wp_term_taxonomy
  ↕
wp_terms
```

### Example:

* Term: "Shoes"
* Taxonomy: `product_cat`
* Post: Product ID `123`

---

## 5️⃣ `wp_options` – Settings & Transients

| Column         | Meaning                  |
| -------------- | ------------------------ |
| `option_name`  | Setting key              |
| `option_value` | Value (often serialized) |
| `autoload`     | `yes` / `no`             |

### Common entries:

* `siteurl`
* `home`
* `active_plugins`
* `_transient_*`
* `_site_transient_*`

⚠️ **Avoid autoload = yes for large values**

---

## 6️⃣ Common SQL Queries

### 🔹 Get published posts

```sql
SELECT * FROM wp_posts
WHERE post_type = 'post'
AND post_status = 'publish';
```

---

### 🔹 Get post meta

```sql
SELECT meta_key, meta_value
FROM wp_postmeta
WHERE post_id = 123;
```

---

### 🔹 Get user roles

```sql
SELECT meta_value
FROM wp_usermeta
WHERE user_id = 1
AND meta_key = 'wp_capabilities';
```

---

### 🔹 Find orphaned postmeta

```sql
SELECT pm.*
FROM wp_postmeta pm
LEFT JOIN wp_posts p ON pm.post_id = p.ID
WHERE p.ID IS NULL;
```

---

### 🔹 Search in content

```sql
SELECT ID, post_title
FROM wp_posts
WHERE post_content LIKE '%keyword%';
```

---

## 7️⃣ WooCommerce-Specific Tables (Quick Look)

| Table                           | Purpose                               |
| ------------------------------- | ------------------------------------- |
| `wp_woocommerce_order_items`    | Order line items                      |
| `wp_woocommerce_order_itemmeta` | Item meta                             |
| `wp_wc_orders`                  | High-performance order storage (HPOS) |
| `wp_wc_customer_lookup`         | Customer data                         |
| `wp_wc_order_stats`             | Order analytics                       |

👉 Modern WooCommerce may **not** rely solely on `wp_posts` for orders.

---

## 8️⃣ Performance & Best Practices

✅ Use WordPress APIs instead of raw SQL:

* `WP_Query`
* `get_post_meta()`
* `get_option()`
* `get_user_meta()`

❌ Avoid:

* Querying `wp_postmeta` with `LIKE`
* Large autoloaded options
* Storing large serialized arrays

✅ Index-heavy sites:

* Add indexes to `meta_key`
* Monitor `wp_options` autoload size

---

## 9️⃣ Debug & Inspection Tips

* Enable DB debug:

```php
define('SAVEQUERIES', true);
```

* Inspect queries:

```php
global $wpdb;
print_r( $wpdb->queries );
```

* Table prefix:

```php
global $wpdb;
echo $wpdb->prefix;
```

