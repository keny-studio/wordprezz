## $${\color{red}WordPress \ Plugins \ and \ Integrations \ Cheat \ Sheet}$$

Common plugins & integrations list — structured by **types, systems, and real-world examples** 

---

### 🏗️ 1. Core Site Foundation

**Purpose:** Performance, structure, environment

**Types:**

* Page Builders / Block Enhancers
* Performance / Caching
* Security
* Backup / Migration

**Examples:**

* Page Builders:

  * Elementor
  * Gutenberg (core + block plugins like Spectra)
  * WPBakery
* Performance:

  * WP Rocket
  * LiteSpeed Cache
  * W3 Total Cache
* Security:

  * Wordfence
  * Sucuri
* Backup:

  * UpdraftPlus
  * All-in-One WP Migration
  * Duplicator

**Dev Notes:**

* Prefer **native Gutenberg + ACF blocks** for scalability
* Avoid stacking multiple caching plugins
* Use staging before backup restores

---

### 🧱 2. Custom Development & Data Layer

**Purpose:** Extend WP as a CMS / application

**Types:**

* Custom Fields / Meta
* Custom Post Types (CPT)
* Data Modeling
* Headless / API

**Examples:**

* ACF (Advanced Custom Fields)
* Meta Box
* Toolset
* CPT UI
* WPGraphQL
* REST API (built-in)

**Dev Notes:**

* ACF + CPT = standard modern WP stack
* Use **JSON sync (ACF)** in Git workflows
* Prefer WPGraphQL for headless React/Vue frontends

---

### 🛒 3. eCommerce Systems

**Purpose:** Selling products/services

**Types:**

* Full eCommerce Platforms
* Payment Gateways
* Subscription Systems
* Booking Systems

**Examples:**

* WooCommerce (core system)
* Payments:

  * Stripe Gateway
  * PayPal
  * Mollie (popular in EU)
* Extensions:

  * Woo Subscriptions
  * Woo Bookings

**Dev Notes:**

* Treat WooCommerce as a **framework**, not just plugin
* Optimize queries (WC can be heavy)
* Use hooks: `woocommerce_before_checkout_form`, etc.

---

### 📈 4. SEO & Marketing Stack

**Purpose:** Visibility, traffic, conversions

**Types:**

* SEO Optimization
* Analytics
* Marketing Automation
* Schema / Structured Data

**Examples:**

* SEO:

  * Yoast SEO
  * Rank Math
* Analytics:

  * Google Analytics (via plugins or GTM)
  * Google Tag Manager plugins
* Marketing:

  * HubSpot WP plugin
  * Mailchimp
* Schema:

  * Schema Pro

**Dev Notes:**

* Avoid multiple SEO plugins at once
* Use **GTM instead of hardcoding scripts**
* Control indexing via `noindex`, robots, canonical

---

### 📬 5. Forms & Data Collection

**Purpose:** User input, leads, workflows

**Types:**

* Contact Forms
* Advanced Forms / Logic
* CRM Integrations

**Examples:**

* Contact Form 7 (lightweight)
* Gravity Forms (advanced)
* WPForms
* Fluent Forms

**Dev Notes:**

* Use **server-side validation + sanitization**
* Integrate with:

  * Zapier
  * HubSpot
  * Webhooks

---

### 🔗 6. Integrations & Automation

**Purpose:** Connect WP with external systems

**Types:**

* Automation Platforms
* API Connectors
* Webhooks

**Examples:**

* Zapier
* Make (Integromat)
* WP Webhooks
* Uncanny Automator

**Dev Notes:**

* Prefer **webhooks over polling**
* Log all outgoing/incoming requests
* Handle retries + failures

---

### 🌍 7. Multilingual & Localization

**Purpose:** Multi-language sites

**Types:**

* Translation Management
* Localization

**Examples:**

* WPML
* Polylang
* TranslatePress

**Dev Notes:**

* WPML = enterprise
* Polylang = lightweight
* Watch for **SEO duplication issues**

---

### 👥 8. User Management & Membership

**Purpose:** Access control, gated content

**Types:**

* Membership Systems
* Role Management
* LMS (Learning Management)

**Examples:**

* MemberPress
* Restrict Content Pro
* LearnDash (LMS)
* User Role Editor

**Dev Notes:**

* Always validate permissions server-side
* Combine with WooCommerce for paid access

---

### 🎨 9. UI / UX Enhancements

**Purpose:** Frontend improvements

**Types:**

* Sliders / Galleries
* UI Components
* Accessibility

**Examples:**

* Slider Revolution
* Swiper (custom integration)
* WP Accessibility

**Dev Notes:**

* Avoid heavy UI plugins when possible
* Prefer custom lightweight components

---

### ⚙️ 10. Developer Utilities

**Purpose:** Improve dev workflow

**Types:**

* Debugging
* Code Management
* CLI tools

**Examples:**

* Query Monitor
* Debug Bar
* WPCode (insert snippets)
* WP-CLI

**Dev Notes:**

* Enable `WP_DEBUG` in dev only
* Use WP-CLI for:

  * migrations
  * cron
  * batch operations

---

### ☁️ 11. Hosting & Infrastructure Integrations

**Purpose:** Deployment & scalability

**Types:**

* CDN
* Cloud Hosting
* CI/CD

**Examples:**

* Cloudflare (CDN + security)
* AWS / DigitalOcean
* Vercel (headless frontends)
* GitHub Actions (CI/CD)

**Dev Notes:**

* Use CDN for static assets
* Separate DB / app for scaling
* Automate deployments

---

### 🔄 Typical Modern WP Stack (Example)

**Content Site (SEO-focused):**

* Gutenberg + ACF
* Rank Math
* WP Rocket
* Cloudflare
* Gravity Forms

**eCommerce Site:**

* WooCommerce
* Stripe / Mollie
* WP Rocket
* ACF (custom product fields)

**Headless WP:**

* WP (backend)
* WPGraphQL
* Next.js frontend
* Cloudflare / Vercel

---

### ⚠️ Best Practices (Critical)

* ❌ Don’t install overlapping plugins (SEO, cache, security)
* ✅ Prefer fewer, well-maintained plugins
* ✅ Audit plugin performance regularly
* ✅ Keep everything updated (plugins, themes, core)
* ✅ Follow **hook-first development** instead of modifying core/plugins
* ✅ Use staging environments

---

### 🧠 Quick Mental Model

Think of WP as:

```
WordPress = CMS Core
+ Data Layer (ACF / CPT)
+ Features (Plugins)
+ Integrations (APIs / Webhooks)
+ Infrastructure (Hosting/CDN)
```
