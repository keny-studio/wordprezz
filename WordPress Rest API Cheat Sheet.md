## $${\color{red}WordPress \ Rest \ API \ Cheat \ Sheet}$$


The **WordPress REST API** is an interface that allows external applications and scripts to **read and manipulate WordPress data using HTTP requests** (usually JSON over REST).

### Key points

* **Protocol:** REST (Representational State Transfer)
* **Data format:** JSON (JavaScript Object Notation)

### What you can do

* Retrieve data: posts, pages, users, comments, categories, tags
* Create, update, delete content (with authentication)
* Build **headless WordPress** sites (WordPress as backend, React/Vue/Next.js as frontend)
* Integrate WordPress with **mobile apps, SaaS tools, or external systems**


### Authentication

* Cookie authentication (same-domain apps)
* Application Passwords (recommended)
* OAuth / JWT (via plugins)

### Use cases

* Headless CMS
* SPA / PWA frontends
* Mobile applications
* WooCommerce & external integrations
* Automation and content sync

### Benefits

* Decouples frontend from backend
* Technology-agnostic
* Built into WordPress core
* Scalable and extensible







---

### Base URL

```text
https://example.com/wp-json/wp/v2/
```

---

## Core Endpoints

### Posts

```http
GET    /posts
GET    /posts/{id}
POST   /posts
PUT    /posts/{id}
DELETE /posts/{id}
```

### Pages

```http
GET /pages
GET /pages/{id}
```

### Users

```http
GET /users
GET /users/{id}
```

### Taxonomies

```http
GET /categories
GET /tags
```

### Media

```http
GET  /media
POST /media
```

---

## Query Parameters

```http
?per_page=10
?page=2
?search=keyword
?slug=post-slug
?status=publish
?orderby=date
?order=desc
?_embed
```

Example:

```http
GET /posts?per_page=5&orderby=date&order=desc
```

---

## Authentication

### Application Passwords (recommended)

```http
Authorization: Basic base64(username:app_password)
```

### Cookie Auth (same domain)

* Requires logged-in user
* Uses WordPress nonce

### JWT / OAuth

* Via plugins

---

## Create Post (Example)

```http
POST /wp-json/wp/v2/posts
```

```json
{
  "title": "My Post",
  "content": "Post content",
  "status": "publish"
}
```

---

## Update Post

```http
PUT /posts/123
```

```json
{
  "title": "Updated title"
}
```

---

## Delete Post

```http
DELETE /posts/123?force=true
```

---

## Custom Post Types

```php
'show_in_rest' => true
```

Access:

```http
/wp-json/wp/v2/{post_type}
```

---

## Custom Fields (Meta)

### Register Meta

```php
register_post_meta('post', 'rating', [
  'show_in_rest' => true,
  'single' => true,
  'type' => 'number'
]);
```

### Use in API

```json
"meta": {
  "rating": 5
}
```

---

## Custom Endpoints

```php
register_rest_route('myplugin/v1', '/data', [
  'methods'  => 'GET',
  'callback' => 'my_callback',
]);
```

URL:

```text
/wp-json/myplugin/v1/data
```

---

## Permissions

```php
'permission_callback' => function () {
  return current_user_can('edit_posts');
}
```

---

## Response Codes

* `200` OK
* `201` Created
* `401` Unauthorized
* `403` Forbidden
* `404` Not Found

---

## Headless Tips

* Use `_embed` to reduce requests
* Cache responses (CDN / Redis)
* Disable unused endpoints for security
* Use WP REST Cache plugin

---
