---
layout: post
title:  WordPress Beginner Interview Questions
tags:
  - WordPress
  - WordPress Developer
  - WordPress Interview Questions
  - WordPress Interview Answers
---


### General WordPress Basics

---

#### **1. What is WordPress?**

**WordPress** is a **Content Management System (CMS)** written in **PHP** that uses a **MySQL** or **MariaDB** database. It helps users create and manage websites without needing to write code.

**Features:**

* Free and open source under GPL
* Highly customizable using plugins and themes
* Supports blogs, ecommerce, portfolios, forums, and more

**How it works:**

1. A visitor requests a page.
2. WordPress loads PHP files.
3. Connects to the database and fetches the required content.
4. Combines content with theme templates.
5. Sends the generated HTML to the browser.

---

#### **2. What are the key differences between WordPress.org and WordPress.com?**

| Feature        | WordPress.org                  | WordPress.com                     |
| -------------- | ------------------------------ | --------------------------------- |
| Hosting        | Self-hosted (your own server)  | Hosted by WordPress.com           |
| Themes/Plugins | Fully customizable             | Restricted unless on paid plans   |
| Coding Access  | Full PHP, CSS, JS access       | Limited access                    |
| Cost           | Free software; pay for hosting | Free for basic use; upgrades cost |

* **Use WordPress.org** if you want full control.
* **Use WordPress.com** for convenience and simplicity.

---

#### **3. How do you install WordPress locally?**

**Steps using XAMPP:**

1. Install XAMPP and start Apache + MySQL.
2. Download WordPress from [wordpress.org](https://wordpress.org/download).
3. Extract it to `htdocs/my-site` inside XAMPP directory.
4. Open `http://localhost/phpmyadmin` and create a database (`my_site_db`).
5. Visit `http://localhost/my-site` and follow the installation wizard.

---

#### **4. What is the wp-content directory used for?**

`wp-content/` holds all the **custom content** added to your site.

**Main subfolders:**

* `themes/` – Your site's design files.
* `plugins/` – Functionality extensions.
* `uploads/` – Media files (images, videos, PDFs).

**Why it matters:**

* This folder is where 90% of customization lives.
* When migrating a site, this is the most important folder to back up.

---

#### **5. What is a plugin in WordPress?**

A **plugin** is a package of PHP code that extends or adds functionality to WordPress.

**Example: Simple Login Logger Plugin**

```php
<?php
/*
Plugin Name: Login Logger
*/

function my_login_logger($user_login, $user) {
    error_log("User '{$user_login}' logged in at " . current_time('mysql'));
}
add_action('wp_login', 'my_login_logger', 10, 2);
```

**How to install:**

* Upload to `wp-content/plugins/`
* Activate via Dashboard > Plugins

---

#### **6. What is a WordPress theme?**

A **theme** defines the **visual design** of a WordPress site. It controls layout, styles, and templates.

**Basic Theme Files:**

* `style.css` – Required stylesheet with theme info.
* `index.php` – Fallback template.
* `functions.php` – Theme configuration.

**Example: style.css**

```css
/*
Theme Name: My Theme
Author: You
Version: 1.0
*/
```

---

#### **7. What does the wp-config.php file do?**

This file sets important **configuration settings**, including:

**Example:**

```php
define('DB_NAME', 'my_database');
define('DB_USER', 'root');
define('DB_PASSWORD', '');
define('DB_HOST', 'localhost');
define('WP_DEBUG', true);
$table_prefix = 'wp_';
```

You should not expose or modify this file carelessly as it contains sensitive data.

---

#### **8. How do you update WordPress to the latest version?**

**Method 1: Dashboard**

* Go to Dashboard > Updates
* Click “Update Now”

**Method 2: WP-CLI**

```bash
wp core update
```

**Precautions:**

* Back up your site.
* Check theme/plugin compatibility.
* Avoid updates on live site during high traffic.

---

#### **9. What is the admin dashboard?**

The admin dashboard is the **backend interface** where site owners manage the site. Accessible via:

```
https://yoursite.com/wp-admin
```

**Core Sections:**

* Posts, Pages, Media
* Appearance
* Plugins
* Settings
* Tools

**Add a custom dashboard widget:**

```php
function my_dashboard_widget() {
    echo "Welcome to your custom dashboard!";
}

function register_my_dashboard_widget() {
    wp_add_dashboard_widget('my_widget', 'My Widget', 'my_dashboard_widget');
}
add_action('wp_dashboard_setup', 'register_my_dashboard_widget');
```

---

#### **10. What is a widget in WordPress?**

Widgets are **modular content blocks** placed in sidebars, footers, or other widget areas.

**Classic Widgets:**

* Go to Appearance > Widgets
* Drag and drop widgets like “Search” or “Recent Posts”

**Create a custom widget (basic version):**

```php
class My_Custom_Widget extends WP_Widget {
    public function __construct() {
        parent::__construct('my_custom_widget', 'My Custom Widget');
    }

    public function widget($args, $instance) {
        echo $args['before_widget'] . 'Hello from my custom widget!' . $args['after_widget'];
    }
}

function register_my_custom_widget() {
    register_widget('My_Custom_Widget');
}
add_action('widgets_init', 'register_my_custom_widget');
```

---

#### **11. What is a shortcode?**

Shortcodes are placeholders for dynamic content. They look like `[my_shortcode]`.

**Define a shortcode using a named function:**

```php
function my_hello_shortcode() {
    return 'Hello, this is a shortcode!';
}
add_shortcode('my_shortcode', 'my_hello_shortcode');
```

**Use in content:**

```text
[my_shortcode]
```

WordPress will output:
`Hello, this is a shortcode!`

---

#### **12. How do you create a page in WordPress?**

**Steps:**

1. Dashboard > Pages > Add New
2. Enter title and content.
3. Click “Publish.”

**Pages vs Posts:**

* Pages are static (About, Contact)
* Not listed by date
* No categories or tags

**Custom Page Template:**

```php
<?php
/* Template Name: Full Width Page */
get_header();
echo '<div>This is a full-width custom template</div>';
get_footer();
```

---

#### **13. How do you set the homepage in WordPress?**

**Steps:**

1. Go to Settings > Reading
2. Under “Your homepage displays”, select “A static page”
3. Choose:

   * Homepage: a page like “Home”
   * Posts page: a page like “Blog”
4. Save changes

Now visitors see the selected page instead of blog posts on the front page.

---

#### **14. What is a permalink?**

A **permalink** is the full, permanent URL to a specific post, page, or resource.

**Examples:**

* Default: `/?p=123`
* Clean: `/my-post/`

**Set under:**
Settings > Permalinks

**Recommended structure for blogs:**

```
/%postname%/
```

**Programmatic access:**

```php
$post_url = get_permalink($post->ID);
```

---

#### **15. What are custom post types?**

Custom Post Types (CPTs) let you define **new content types** beyond Posts and Pages.

**Example: Portfolio items**

**Register CPT using named function:**

```php
function register_portfolio_post_type() {
    $args = array(
        'label' => 'Portfolio',
        'public' => true,
        'supports' => array('title', 'editor', 'thumbnail'),
        'has_archive' => true,
        'menu_icon' => 'dashicons-portfolio'
    );
    register_post_type('portfolio', $args);
}
add_action('init', 'register_portfolio_post_type');
```

**What this does:**

* Adds "Portfolio" to dashboard
* Enables new content structure
* Archives accessible at `/portfolio/`

---


### Theme Development Basics

---

#### **1. What files are required to create a basic WordPress theme?**

To create a **minimal but functional WordPress theme**, you need **at least two files**:

1. **style.css** – contains the theme metadata and styling.
2. **index.php** – the main template file.

**Optional (but recommended) files:**

* `functions.php` – theme setup and feature support.
* `screenshot.png` – a preview image shown in the admin.
* `header.php`, `footer.php`, `sidebar.php` – template parts for structure.
* `single.php`, `page.php`, `archive.php` – to handle specific views.

**style.css example:**

```css
/*
Theme Name: My First Theme
Author: Your Name
Version: 1.0
*/
```

---

#### **2. What is the use of style.css in a WordPress theme?**

`style.css` serves **two roles**:

1. **Metadata declaration** – Required header comment that tells WordPress the theme’s name, author, version, etc.
2. **Main stylesheet** – Contains CSS rules for styling the theme.

**Example content:**

```css
/*
Theme Name: Custom Starter Theme
Author: Jane Doe
Version: 1.0
*/

body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
}
```

WordPress uses this file to recognize and list your theme in the dashboard.

---

#### **3. What is the functions.php file used for?**

`functions.php` is like the **engine room** of your theme. It is loaded automatically when the theme is active.

You use it to:

* Register theme features
* Enqueue styles/scripts
* Register menus, sidebars
* Add filters and actions

**Example:**

```php
function mytheme_setup() {
    add_theme_support('title-tag');
    add_theme_support('post-thumbnails');
}
add_action('after_setup_theme', 'mytheme_setup');
```

---

#### **4. How do you enqueue styles and scripts in WordPress?**

Never use `<link>` or `<script>` tags directly. Use **`wp_enqueue_style()`** and **`wp_enqueue_script()`**.

**Correct way:**

```php
function mytheme_enqueue_assets() {
    wp_enqueue_style('mytheme-style', get_stylesheet_uri());
    wp_enqueue_script('mytheme-script', get_template_directory_uri() . '/assets/js/script.js', array(), '1.0', true);
}
add_action('wp_enqueue_scripts', 'mytheme_enqueue_assets');
```

**Why enqueueing is important:**

* Prevents conflicts
* Avoids duplicate loading
* Enables dependency management

---

#### **5. What is the purpose of get\_header() and get\_footer()?**

These functions **include partial template files**:

* `get_header()` loads `header.php`
* `get_footer()` loads `footer.php`

They’re used in main templates to follow DRY (Don’t Repeat Yourself) principles.

**Example in index.php:**

```php
get_header();

echo '<main>';
if (have_posts()) {
    while (have_posts()) {
        the_post();
        the_content();
    }
}
echo '</main>';

get_footer();
```

---

#### **6. What is the template hierarchy in WordPress?**

The **template hierarchy** is the system WordPress uses to determine which theme file to load for different types of content.

**Examples:**

* A post: `single-post.php` → `single.php` → `singular.php` → `index.php`
* A page: `page-{slug}.php` → `page-{id}.php` → `page.php` → `singular.php` → `index.php`
* A category: `category-{slug}.php` → `category.php` → `archive.php` → `index.php`

WordPress starts with the **most specific file** and falls back to more general ones.

---

#### **7. How do you create a custom page template?**

You can define a custom template for individual pages by adding a comment at the top of a new PHP file in your theme.

**Example: `page-custom.php`**

```php
<?php
/*
Template Name: Custom Landing Page
*/
get_header();
echo '<h1>This is a custom page template</h1>';
get_footer();
```

**How to use:**

1. Create a page in the admin
2. Select "Custom Landing Page" from the Template dropdown (in Page Attributes)

---

#### **8. What is the\_content() function?**

`the_content()` outputs the **main body content** of a post or page from the database.

**Usage:**

```php
if (have_posts()) {
    while (have_posts()) {
        the_post();
        the_content(); // outputs post/page content
    }
}
```

**Note:**
It applies filters like shortcodes, paragraph formatting, and block rendering.

If you just want the raw content (without output), use `get_the_content()`.

---

#### **9. What is get\_template\_part() used for?**

`get_template_part()` is used to **include reusable template parts** (e.g., post layout, content blocks).

**Usage:**

```php
get_template_part('template-parts/content', 'single');
```

This looks for:

* `template-parts/content-single.php`
* If not found: `template-parts/content.php`

**Benefits:**

* Cleaner code
* Easy to reuse sections
* Follows separation of concerns

---

#### **10. How do you create a custom sidebar?**

You register a sidebar using `register_sidebar()` in `functions.php`.

**Step 1: Register Sidebar**

```php
function mytheme_widgets_init() {
    register_sidebar(array(
        'name' => 'Main Sidebar',
        'id' => 'main_sidebar',
        'before_widget' => '<section class="widget">',
        'after_widget' => '</section>',
        'before_title' => '<h3>',
        'after_title' => '</h3>',
    ));
}
add_action('widgets_init', 'mytheme_widgets_init');
```

**Step 2: Display in Template**

```php
if (is_active_sidebar('main_sidebar')) {
    dynamic_sidebar('main_sidebar');
}
```

---

#### **11. How can you make a theme translation-ready?**

To prepare your theme for translation:

**Step 1: Add this in `functions.php`:**

```php
function mytheme_load_textdomain() {
    load_theme_textdomain('mytheme', get_template_directory() . '/languages');
}
add_action('after_setup_theme', 'mytheme_load_textdomain');
```

**Step 2: Wrap all text with translation functions**

```php
_e('Read more', 'mytheme');
```

**Step 3: Create a `.pot` file**
Use tools like **Poedit** or **Loco Translate** to generate translatable strings.

---

#### **12. What is the wp\_head() function?**

`wp_head()` is a core WordPress function that **outputs important code in the `<head>` section** of your HTML.

You must call it in `header.php` just before `</head>`:

```php
<head>
    <meta charset="<?php bloginfo('charset'); ?>">
    <?php wp_head(); ?>
</head>
```

**What it does:**

* Outputs enqueued styles/scripts
* Injects meta tags
* Adds plugin code (like SEO tags)

Without this, many plugins and features won’t work properly.

---

#### **13. How do you add a featured image to a post?**

**Step 1: Enable in `functions.php`:**

```php
function mytheme_enable_thumbnails() {
    add_theme_support('post-thumbnails');
}
add_action('after_setup_theme', 'mytheme_enable_thumbnails');
```

**Step 2: Set in Post Editor**

* Edit a post
* Set a featured image using the right sidebar

**Step 3: Display in template**

```php
if (has_post_thumbnail()) {
    the_post_thumbnail('medium'); // sizes: thumbnail, medium, large
}
```

---

#### **14. How do you create a navigation menu?**

**Step 1: Register Menu in `functions.php`:**

```php
function mytheme_register_menus() {
    register_nav_menu('main_menu', 'Main Navigation Menu');
}
add_action('after_setup_theme', 'mytheme_register_menus');
```

**Step 2: Assign it in Dashboard**
Appearance > Menus > Create and assign menu to “Main Navigation Menu”

**Step 3: Display it in template**

```php
wp_nav_menu(array(
    'theme_location' => 'main_menu',
    'menu_class' => 'nav-menu'
));
```

---

#### **15. How do you use is\_page() and is\_single()?**

These are **conditional functions** used to check the current post/page type.

**`is_page()`** – returns true if viewing a specific page
**`is_single()`** – returns true if viewing a blog post

**Examples:**

```php
function my_custom_body_class($classes) {
    if (is_page('about')) {
        $classes[] = 'about-page';
    }
    if (is_single() && has_category('news')) {
        $classes[] = 'news-post';
    }
    return $classes;
}
add_filter('body_class', 'my_custom_body_class');
```

You can also pass page/post IDs or slugs:

```php
is_page(42)
is_page('contact')
is_single('hello-world')
```

---

### Plugin Development Basics

---

#### **1. How do you create a basic WordPress plugin?**

A WordPress plugin is simply a PHP file with a special comment header, placed inside the `wp-content/plugins/` directory.

**Steps:**

1. Create a folder: `wp-content/plugins/my-first-plugin`
2. Inside it, create a PHP file: `my-first-plugin.php`

**Example:**

```php
<?php
/**
 * Plugin Name: My First Plugin
 * Description: A simple plugin to display a message.
 * Version: 1.0
 * Author: Your Name
 */

function myfp_display_message() {
    echo '<p>Hello from My First Plugin!</p>';
}
add_action('wp_footer', 'myfp_display_message');
```

Then activate it via Dashboard > Plugins.

---

#### **2. What is the plugin header comment?**

The **plugin header comment** is a block of metadata required by WordPress to recognize a plugin.

It must appear at the top of the main plugin file.

**Example:**

```php
/*
Plugin Name: Custom Widget Plugin
Plugin URI: https://example.com/custom-widget
Description: Adds a custom widget to the sidebar.
Version: 1.0
Author: John Doe
Author URI: https://example.com
License: GPL2
*/
```

This header allows WordPress to display plugin details in the admin area.

---

#### **3. What is `add_action()` in WordPress?**

`add_action()` connects your custom function to a **specific action hook** in WordPress.

It tells WordPress: “When this event happens, run this function.”

**Example:**

```php
function myplugin_footer_text() {
    echo '<p>This site is powered by MyPlugin.</p>';
}
add_action('wp_footer', 'myplugin_footer_text');
```

In this case, when `wp_footer` is called in the theme, your function is executed.

---

#### **4. What is `add_filter()`?**

`add_filter()` is used to **modify data** before it is displayed or saved.

**Example:**

```php
function myplugin_change_title($title) {
    return '🔥 ' . $title;
}
add_filter('the_title', 'myplugin_change_title');
```

This prepends a fire icon to every post title.

---

#### **5. What are WordPress hooks?**

Hooks are predefined **points in WordPress execution** where you can add or modify behavior.

There are two types:

* **Actions**: Do something (e.g., insert HTML, send email)
* **Filters**: Modify data (e.g., change post title)

**Example hooks:**

* `wp_footer` (action)
* `the_content` (filter)
* `init` (action)
* `excerpt_length` (filter)

Hooks allow plugins and themes to **interact with WordPress core without modifying it**.

---

#### **6. What is the difference between actions and filters?**

| Feature      | Actions                        | Filters                         |
| ------------ | ------------------------------ | ------------------------------- |
| Purpose      | Execute logic                  | Modify data                     |
| Return value | None                           | Must return modified value      |
| Example hook | `wp_head`, `init`, `save_post` | `the_title`, `content_save_pre` |

**Action Example:**

```php
function myplugin_on_init() {
    // Run some custom logic on init
}
add_action('init', 'myplugin_on_init');
```

**Filter Example:**

```php
function myplugin_modify_title($title) {
    return 'Modified: ' . $title;
}
add_filter('the_title', 'myplugin_modify_title');
```

---

#### **7. How do you register a custom shortcode?**

Use `add_shortcode()` with a **named function** that returns content.

**Example:**

```php
function myplugin_hello_shortcode() {
    return '<p>Hello from shortcode!</p>';
}
add_shortcode('hello', 'myplugin_hello_shortcode');
```

Use it in content:

```text
[hello]
```

This will output:

```
Hello from shortcode!
```

---

#### **8. What is `register_activation_hook()` used for?**

This function runs **only once** — when the plugin is activated.

Common uses:

* Create database tables
* Set default options

**Example:**

```php
function myplugin_on_activation() {
    update_option('myplugin_enabled', true);
}
register_activation_hook(__FILE__, 'myplugin_on_activation');
```

You must call this in the **main plugin file**.

---

#### **9. How can you include custom CSS/JS in a plugin?**

Use `wp_enqueue_style()` and `wp_enqueue_script()` **inside a function** and hook it to `wp_enqueue_scripts`.

**Example:**

```php
function myplugin_enqueue_assets() {
    wp_enqueue_style('myplugin-style', plugin_dir_url(__FILE__) . 'assets/style.css');
    wp_enqueue_script('myplugin-script', plugin_dir_url(__FILE__) . 'assets/script.js', array(), '1.0', true);
}
add_action('wp_enqueue_scripts', 'myplugin_enqueue_assets');
```

Make sure `style.css` and `script.js` exist in the plugin’s `/assets/` folder.

---

#### **10. What is a nonce in WordPress?**

A **nonce** (Number used once) is a token used to **verify that a request came from a legitimate source**. It protects against **CSRF (Cross-Site Request Forgery)**.

**Create nonce for a form:**

```php
wp_nonce_field('myplugin_action', 'myplugin_nonce');
```

**Verify it in PHP:**

```php
if (!isset($_POST['myplugin_nonce']) || !wp_verify_nonce($_POST['myplugin_nonce'], 'myplugin_action')) {
    wp_die('Invalid request');
}
```

Nonces expire after 24 hours by default.

---

#### **11. How do you sanitize input in a plugin?**

Always sanitize user input before using it.

**Common functions:**

* `sanitize_text_field()`
* `sanitize_email()`
* `absint()`
* `esc_url()`

**Example:**

```php
function myplugin_save_name($name_input) {
    $name = sanitize_text_field($name_input);
    update_option('myplugin_name', $name);
}
```

Sanitizing prevents XSS, database injection, and other vulnerabilities.

---

#### **12. How do you register a custom settings page?**

You can create a settings page in the admin using `add_menu_page()`.

**Step 1: Register Page**

```php
function myplugin_admin_menu() {
    add_menu_page(
        'My Plugin Settings',
        'My Plugin',
        'manage_options',
        'myplugin-settings',
        'myplugin_render_settings_page'
    );
}
add_action('admin_menu', 'myplugin_admin_menu');
```

**Step 2: Define Callback**

```php
function myplugin_render_settings_page() {
    echo '<div class="wrap"><h1>Plugin Settings</h1></div>';
}
```

You can expand this with form inputs and saving logic.

---

#### **13. What is the use of the `admin_menu` hook?**

The `admin_menu` hook is used to **add items to the WordPress admin menu**.

**Examples:**

* Create custom settings pages
* Add submenus under existing menus
* Control menu visibility with roles

**Usage:**

```php
add_action('admin_menu', 'myplugin_add_menu');

function myplugin_add_menu() {
    add_menu_page('Title', 'My Menu', 'manage_options', 'myplugin', 'myplugin_render_page');
}
```

---

#### **14. How do you handle form submissions in a plugin?**

**1. Display form with nonce:**

```php
function myplugin_form_output() {
    echo '<form method="post">';
    wp_nonce_field('myplugin_submit', 'myplugin_nonce');
    echo '<input type="text" name="my_name">';
    echo '<input type="submit" name="submit_button">';
    echo '</form>';
}
```

**2. Handle form data:**

```php
function myplugin_process_form() {
    if (isset($_POST['submit_button']) && check_admin_referer('myplugin_submit', 'myplugin_nonce')) {
        $name = sanitize_text_field($_POST['my_name']);
        update_option('myplugin_saved_name', $name);
    }
}
add_action('admin_init', 'myplugin_process_form');
```

Always sanitize input and verify nonces.

---

#### **15. What is `wp_enqueue_script()`?**

This function **adds JavaScript files to WordPress pages** in a proper, safe, and dependency-aware way.

**Syntax:**

```php
wp_enqueue_script(
    $handle,            // unique name
    $src,               // path to script
    $deps = array(),    // dependencies (e.g. ['jquery'])
    $ver = false,       // version number
    $in_footer = false  // load in footer?
);
```

**Example:**

```php
function myplugin_load_scripts() {
    wp_enqueue_script('myplugin-js', plugin_dir_url(__FILE__) . 'assets/main.js', array('jquery'), '1.0', true);
}
add_action('wp_enqueue_scripts', 'myplugin_load_scripts');
```

This ensures:

* No duplicate loading
* Script runs in the right place
* Dependency like jQuery is loaded first

---

Database and Core Functions

---

#### **1. What is the default table prefix in WordPress?**

The default table prefix is:

```text
wp_
```

So WordPress creates tables like:

* `wp_posts`
* `wp_users`
* `wp_options`

You can customize the prefix during installation (for example, `abc_`). This helps **avoid conflicts** and slightly improves **security** by obscuring default table names.

---

#### **2. How do you access the database in WordPress?**

WordPress provides an object called **`$wpdb`** to access the database.

You don’t need to write raw MySQL code or connect manually. `$wpdb` handles:

* Safe queries
* Prepared statements
* Table prefixes

**Basic usage:**

```php
function get_total_post_count() {
    global $wpdb;
    $count = $wpdb->get_var("SELECT COUNT(*) FROM {$wpdb->posts} WHERE post_type = 'post'");
    return $count;
}
```

---

#### **3. What is `$wpdb`?**

`$wpdb` is a **WordPress global object** that provides an interface to interact with the WordPress database.

It is an instance of the `wpdb` class and gives access to methods like:

* `get_results()`
* `get_var()`
* `insert()`
* `update()`
* `delete()`
* `prepare()`

It also holds all table names with the correct prefix, like `$wpdb->posts`, `$wpdb->users`, `$wpdb->options`.

**Example:**

```php
function get_post_titles() {
    global $wpdb;
    return $wpdb->get_col("SELECT post_title FROM {$wpdb->posts} WHERE post_status = 'publish'");
}
```

---

#### **4. How do you write a custom SQL query in WordPress?**

Use `$wpdb` to write safe and efficient SQL queries. Use `prepare()` to avoid SQL injection.

**Example:**

```php
function get_author_posts($author_id) {
    global $wpdb;
    $sql = $wpdb->prepare("SELECT post_title FROM {$wpdb->posts} WHERE post_author = %d AND post_status = 'publish'", $author_id);
    return $wpdb->get_col($sql);
}
```

* `%d` for integers
* `%s` for strings

Always use `prepare()` when inserting variables into SQL queries.

---

#### **5. What is the purpose of `get_option()` and `update_option()`?**

These functions allow you to **retrieve and store settings** in the `wp_options` table.

* `get_option( $name )`: retrieves a value
* `update_option( $name, $value )`: saves or updates a value

**Example:**

```php
function save_plugin_setting() {
    update_option('myplugin_enabled', true);
}

function get_plugin_setting() {
    return get_option('myplugin_enabled');
}
```

Use these for plugin settings, theme options, and general configurations.

---

#### **6. How do you add a custom meta field to posts?**

Use `add_post_meta()` to add new meta or `update_post_meta()` to update it.

**Example:**

```php
function set_reading_time($post_id, $minutes) {
    update_post_meta($post_id, 'reading_time', absint($minutes));
}
```

To retrieve it:

```php
function get_reading_time($post_id) {
    return get_post_meta($post_id, 'reading_time', true);
}
```

Meta fields are stored in `wp_postmeta`.

---

#### **7. What are post meta and user meta?**

Both are types of **custom fields** attached to posts or users:

* **Post Meta**: Data related to a post (e.g., `reading_time`, `featured_color`)

  * Stored in `wp_postmeta`
  * Use: `add_post_meta()`, `get_post_meta()`

* **User Meta**: Data related to users (e.g., `phone_number`, `profile_visibility`)

  * Stored in `wp_usermeta`
  * Use: `add_user_meta()`, `get_user_meta()`

**Example:**

```php
function set_user_bio($user_id, $bio) {
    update_user_meta($user_id, 'custom_bio', sanitize_text_field($bio));
}
```

---

#### **8. How do you create a custom table in WordPress?**

Use `dbDelta()` inside `register_activation_hook()` to safely create tables.

**Example:**

```php
function myplugin_create_table() {
    global $wpdb;
    $table = $wpdb->prefix . 'my_custom_table';
    $charset = $wpdb->get_charset_collate();

    $sql = "CREATE TABLE $table (
        id BIGINT(20) UNSIGNED NOT NULL AUTO_INCREMENT,
        name VARCHAR(255) NOT NULL,
        created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
        PRIMARY KEY (id)
    ) $charset;";

    require_once ABSPATH . 'wp-admin/includes/upgrade.php';
    dbDelta($sql);
}

register_activation_hook(__FILE__, 'myplugin_create_table');
```

Always include `upgrade.php` and use `dbDelta()` for safe, update-aware table creation.

---

#### **9. What is a transient in WordPress?**

A **transient** is a way to store **temporary data in the database** with an expiration time.

Useful for caching expensive queries or API responses.

**Set transient:**

```php
function store_api_response($data) {
    set_transient('api_cache_key', $data, HOUR_IN_SECONDS);
}
```

**Get transient:**

```php
function get_cached_api_data() {
    return get_transient('api_cache_key');
}
```

**Delete transient:**

```php
delete_transient('api_cache_key');
```

Stored in the `wp_options` table with an `_transient_` prefix.

---

#### **10. How do you delete a WordPress option?**

Use `delete_option()` to permanently remove an option from the `wp_options` table.

**Example:**

```php
function remove_plugin_option() {
    delete_option('myplugin_enabled');
}
```

If the option doesn’t exist, WordPress simply skips it without error.

---

#### **11. What is the difference between `get_post_meta()` and `get_option()`?**

| Function          | Purpose                                 | Table Used    |
| ----------------- | --------------------------------------- | ------------- |
| `get_post_meta()` | Retrieves custom fields for posts/pages | `wp_postmeta` |
| `get_option()`    | Retrieves site-wide settings            | `wp_options`  |

Use `get_post_meta()` when the data is tied to a **specific post or page**.
Use `get_option()` for **global plugin or theme settings**.

---

#### **12. How can you import data into WordPress programmatically?**

Use functions like `wp_insert_post()`, `wp_insert_user()`, `update_post_meta()`.

**Example: Add posts from an array**

```php
function import_blog_posts($posts) {
    foreach ($posts as $post_data) {
        $post_id = wp_insert_post(array(
            'post_title'   => $post_data['title'],
            'post_content' => $post_data['content'],
            'post_status'  => 'publish',
            'post_type'    => 'post'
        ));
        update_post_meta($post_id, 'source', 'imported');
    }
}
```

Always sanitize and validate incoming data before saving.

---

#### **13. What is `wp_insert_post()`?**

This function **adds or updates a post** in the database.

**Example:**

```php
function create_new_post() {
    $post_id = wp_insert_post(array(
        'post_title'   => 'My New Post',
        'post_content' => 'This is the content.',
        'post_status'  => 'publish',
        'post_type'    => 'post'
    ));
    return $post_id;
}
```

You can use it for posts, pages, or custom post types.
If `ID` is included in the array, it will **update** that post instead of creating a new one.

---

#### **14. How do you check if a post exists in the database?**

Check using `get_page_by_title()`, `get_post()`, or a custom query.

**Example: Check by title**

```php
function does_post_exist($title) {
    $existing_post = get_page_by_title($title, OBJECT, 'post');
    return $existing_post ? $existing_post->ID : false;
}
```

Or check by ID:

```php
function is_post_valid($post_id) {
    return get_post($post_id) !== null;
}
```

---

#### **15. What is the use of `prepare()` method with `$wpdb`?**

`$wpdb->prepare()` is used to **safely insert variables into SQL queries** and **prevent SQL injection**.

**Syntax:**

```php
$wpdb->prepare( $query, $value1, $value2 );
```

**Example:**

```php
function get_posts_by_author($author_id) {
    global $wpdb;
    $sql = $wpdb->prepare("SELECT * FROM {$wpdb->posts} WHERE post_author = %d", $author_id);
    return $wpdb->get_results($sql);
}
```

Placeholders:

* `%d` for integers
* `%s` for strings
* `%f` for floats

Always use `prepare()` when inserting user input into SQL.

---

### WooCommerce Basics

---

#### **1. What is WooCommerce?**

WooCommerce is a **free WordPress plugin** that transforms your WordPress site into a **fully functional ecommerce store**.

**What it does:**

* Lets you sell physical and digital products
* Manages inventory, taxes, shipping
* Supports payments (PayPal, Stripe, UPI, etc.)
* Offers thousands of add-ons (subscriptions, bookings, memberships)

Built by Automattic, it’s the most popular ecommerce solution for WordPress.

---

#### **2. How do you install WooCommerce on a WordPress site?**

**Steps:**

1. Go to **Plugins > Add New**
2. Search for **WooCommerce**
3. Click **Install Now** → then **Activate**

After activation:

* WooCommerce creates pages: Shop, Cart, Checkout, My Account
* A setup wizard will guide you through currency, shipping, and payment settings

---

#### **3. What is a WooCommerce product?**

A **product** in WooCommerce is a **post of the `product` custom post type**. Each product contains:

* Title
* Description
* Price
* Inventory status
* Categories and tags
* Product type (simple, variable, etc.)

Products are stored in the `wp_posts` table and extended using `postmeta`.

---

#### **4. What are the different product types in WooCommerce?**

WooCommerce supports the following **product types**:

1. **Simple Product** – A physical item with no variations
2. **Variable Product** – Has variations like size or color
3. **Grouped Product** – Collection of simple products sold together
4. **External/Affiliate Product** – Links to another website
5. **Downloadable Product** – Digital files
6. **Virtual Product** – Services or non-physical items

Each type is handled differently in the backend and checkout logic.

---

#### **5. How do you create a simple product in code?**

You can use `wp_insert_post()` and `update_post_meta()` to create a WooCommerce product.

**Example:**

```php
function create_simple_woo_product() {
    $post_id = wp_insert_post(array(
        'post_title'   => 'Test Product',
        'post_content' => 'This is a test product.',
        'post_status'  => 'publish',
        'post_type'    => 'product'
    ));

    update_post_meta($post_id, '_regular_price', '29.99');
    update_post_meta($post_id, '_price', '29.99');
    update_post_meta($post_id, '_stock_status', 'instock');
}
```

---

#### **6. How can you customize the "Add to Cart" button text?**

Use the `woocommerce_product_single_add_to_cart_text` and `woocommerce_product_add_to_cart_text` filters.

**Example:**

```php
function custom_add_to_cart_button_text() {
    return 'Buy Now';
}
add_filter('woocommerce_product_single_add_to_cart_text', 'custom_add_to_cart_button_text');
add_filter('woocommerce_product_add_to_cart_text', 'custom_add_to_cart_button_text');
```

Applies to both archive and single product pages.

---

#### **7. What are WooCommerce hooks?**

WooCommerce hooks are similar to WordPress hooks—**they let you run custom code or modify output at specific points** in WooCommerce templates or processes.

Two types:

* **Actions** – Add custom HTML or logic (`add_action`)
* **Filters** – Modify values (`add_filter`)

**Examples:**

* `woocommerce_before_main_content`
* `woocommerce_add_cart_item_data`
* `woocommerce_cart_calculate_fees`

---

#### **8. What is the function of `woocommerce_before_main_content`?**

This is an **action hook** fired at the **beginning of the content area** on shop-related pages (shop, single product, category).

Used to:

* Insert banners, breadcrumbs, custom notices
* Wrap content in layout markup

**Example:**

```php
function add_custom_banner_before_products() {
    echo '<div class="banner">Summer Sale is Live!</div>';
}
add_action('woocommerce_before_main_content', 'add_custom_banner_before_products');
```

---

#### **9. How do you enqueue styles in a WooCommerce-compatible theme?**

WooCommerce-compatible themes use `add_theme_support( 'woocommerce' )` and enqueue their own styles using `wp_enqueue_style`.

**Step 1: Declare compatibility in `functions.php`:**

```php
function mytheme_add_woocommerce_support() {
    add_theme_support('woocommerce');
}
add_action('after_setup_theme', 'mytheme_add_woocommerce_support');
```

**Step 2: Enqueue styles:**

```php
function mytheme_enqueue_woo_styles() {
    if (class_exists('WooCommerce')) {
        wp_enqueue_style('mytheme-woocommerce', get_template_directory_uri() . '/css/woocommerce.css');
    }
}
add_action('wp_enqueue_scripts', 'mytheme_enqueue_woo_styles');
```

---

#### **10. How do you override WooCommerce templates?**

**Steps:**

1. Copy the WooCommerce template from:
   `wp-content/plugins/woocommerce/templates/`

2. Paste it into your theme like:
   `yourtheme/woocommerce/single-product/title.php`

3. Modify as needed.

WooCommerce will load the template from the theme directory instead of its default location.

Always maintain directory structure.

---

#### **11. What file handles the single product layout?**

The main file is:

```text
woocommerce/single-product.php
```

It includes partials like:

* `title.php`
* `price.php`
* `add-to-cart/simple.php`
* `tabs/tabs.php`

You can override each part by copying the corresponding file into your theme’s `woocommerce` folder.

---

#### **12. How do you add a custom tab to the product page?**

Use the `woocommerce_product_tabs` filter.

**Example:**

```php
function add_custom_product_tab($tabs) {
    $tabs['custom_tab'] = array(
        'title'    => 'More Info',
        'priority' => 50,
        'callback' => 'render_custom_product_tab_content'
    );
    return $tabs;
}
add_filter('woocommerce_product_tabs', 'add_custom_product_tab');

function render_custom_product_tab_content() {
    echo '<p>This is extra info added via a custom tab.</p>';
}
```

---

#### **13. How can you add a custom fee during checkout?**

Hook into `woocommerce_cart_calculate_fees`.

**Example:**

```php
function add_handling_fee_to_checkout($cart) {
    if (is_admin() && !defined('DOING_AJAX')) return;
    $cart->add_fee('Handling Fee', 5.00);
}
add_action('woocommerce_cart_calculate_fees', 'add_handling_fee_to_checkout');
```

This adds a fixed fee visible on the checkout page.

---

#### **14. What is the function to get the cart total?**

Use:

```php
WC()->cart->get_total();        // Formatted string with currency
WC()->cart->get_cart_total();  // Similar to get_total()
WC()->cart->get_cart_contents_total(); // Numeric value without tax/shipping
```

**Example:**

```php
function show_cart_total_notice() {
    $total = WC()->cart->get_cart_contents_total();
    wc_add_notice("Cart subtotal: ₹" . $total, 'notice');
}
add_action('woocommerce_before_checkout_form', 'show_cart_total_notice');
```

---

#### **15. How do you programmatically create an order?**

Use the `WC_Order` class.

**Example:**

```php
function create_programmatic_order() {
    $address = array(
        'first_name' => 'John',
        'last_name'  => 'Doe',
        'email'      => 'john@example.com',
        'address_1'  => '123 Street',
        'city'       => 'Calicut',
        'postcode'   => '673001',
        'country'    => 'IN'
    );

    $order = wc_create_order();
    $order->add_product(wc_get_product(123), 1); // Product ID, quantity
    $order->set_address($address, 'billing');
    $order->calculate_totals();
    $order->update_status('processing');

    return $order->get_id();
}
```

This creates an order, adds a product, and sets billing details.

---

### JavaScript & jQuery in WordPress

---

#### **1. How do you enqueue a JavaScript file in WordPress?**

To add a JavaScript file properly, use `wp_enqueue_script()` inside a function, then hook it to `wp_enqueue_scripts`.

**Example:**

```php
function enqueue_custom_script() {
    wp_enqueue_script(
        'custom-js', 
        get_template_directory_uri() . '/js/custom.js', 
        array('jquery'), 
        '1.0.0', 
        true // Load in footer
    );
}
add_action('wp_enqueue_scripts', 'enqueue_custom_script');
```

* `array('jquery')` sets jQuery as a dependency.
* `true` loads the script in the footer for better performance.

---

#### **2. What is `wp_localize_script()` used for?**

`wp_localize_script()` is used to **pass PHP data to JavaScript** — especially useful for AJAX URLs and nonces.

**Example:**

```php
function localize_ajax_data() {
    wp_enqueue_script('custom-js', get_template_directory_uri() . '/js/custom.js', array('jquery'), null, true);

    $ajax_data = array(
        'ajax_url' => admin_url('admin-ajax.php'),
        'nonce'    => wp_create_nonce('custom_nonce')
    );

    wp_localize_script('custom-js', 'my_ajax_obj', $ajax_data);
}
add_action('wp_enqueue_scripts', 'localize_ajax_data');
```

In your `custom.js`:

```javascript
console.log(my_ajax_obj.ajax_url);
```

---

#### **3. How do you make a simple AJAX request in WordPress?**

**Step 1: Localize script with `admin-ajax.php` and nonce** (as shown above).

**Step 2: JavaScript/jQuery AJAX**

```javascript
jQuery(document).ready(function($) {
    $('#getData').on('click', function() {
        $.ajax({
            url: my_ajax_obj.ajax_url,
            method: 'POST',
            data: {
                action: 'fetch_data',
                security: my_ajax_obj.nonce
            },
            success: function(response) {
                $('#result').html(response);
            }
        });
    });
});
```

**Step 3: Handle it in PHP**

```php
function handle_ajax_request() {
    check_ajax_referer('custom_nonce', 'security');

    echo 'This is data from PHP!';
    wp_die();
}
add_action('wp_ajax_fetch_data', 'handle_ajax_request');
add_action('wp_ajax_nopriv_fetch_data', 'handle_ajax_request');
```

---

#### **4. How do you pass a nonce to JavaScript?**

Use `wp_create_nonce()` to generate the nonce, and `wp_localize_script()` to pass it.

**PHP:**

```php
function pass_nonce_to_js() {
    wp_enqueue_script('my-js', get_template_directory_uri() . '/js/my.js', array('jquery'), null, true);

    $nonce_data = array(
        'nonce' => wp_create_nonce('secure_action')
    );

    wp_localize_script('my-js', 'my_nonce_obj', $nonce_data);
}
add_action('wp_enqueue_scripts', 'pass_nonce_to_js');
```

**JavaScript:**

```javascript
var nonce = my_nonce_obj.nonce;
```

Use it in AJAX for security validation.

---

#### **5. What is the `admin-ajax.php` file?**

`admin-ajax.php` is a **core WordPress file** that handles **AJAX requests** on both front end and admin.

AJAX URL:

```php
admin_url('admin-ajax.php')
```

Common use:

* Define an `action` value
* Use `add_action('wp_ajax_...')` and optionally `wp_ajax_nopriv_...`

This allows plugin or theme developers to process AJAX safely and within WordPress.

---

#### **6. How do you detect if jQuery is loaded in your theme?**

You can:

1. Check the source code (`view-source:` or dev tools) for a jQuery `<script>` tag.
2. Run this in the browser console:

```javascript
typeof jQuery !== 'undefined' // should return true
```

**Proper way to include jQuery in your theme:**

```php
function ensure_jquery_loaded() {
    wp_enqueue_script('jquery');
}
add_action('wp_enqueue_scripts', 'ensure_jquery_loaded');
```

This loads WordPress’s built-in version of jQuery.

---

#### **7. What is the difference between `$(document).ready()` and `window.onload`?**

| Feature      | `$(document).ready()`            | `window.onload`                               |
| ------------ | -------------------------------- | --------------------------------------------- |
| Trigger time | When DOM is fully loaded         | When entire page is loaded (including images) |
| Scope        | jQuery                           | Native JS                                     |
| Performance  | Faster (runs before images load) | Slower (waits for everything)                 |

**Example using jQuery:**

```javascript
jQuery(document).ready(function($) {
    // Safe to manipulate DOM here
});
```

---

#### **8. How do you add click event listeners with jQuery?**

Use the `.on()` method for attaching event listeners.

**Example:**

```javascript
jQuery(document).ready(function($) {
    $('#myButton').on('click', function() {
        alert('Button clicked!');
    });
});
```

Using `.on()` is preferred over `.click()` because it's compatible with dynamically added elements.

---

#### **9. How do you safely load jQuery in a WordPress theme?**

Use `wp_enqueue_script()` and declare `'jquery'` as a dependency.

**Example:**

```php
function load_jquery_in_theme() {
    wp_enqueue_script('theme-js', get_template_directory_uri() . '/js/theme.js', array('jquery'), null, true);
}
add_action('wp_enqueue_scripts', 'load_jquery_in_theme');
```

This ensures WordPress loads jQuery **only once** and in the correct order.

---

#### **10. How can you submit a form via AJAX?**

**Step 1: Add the form in HTML**

```html
<form id="contactForm">
    <input type="text" name="name" required />
    <input type="submit" value="Send" />
</form>
<div id="response"></div>
```

**Step 2: JavaScript**

```javascript
jQuery(document).ready(function($) {
    $('#contactForm').on('submit', function(e) {
        e.preventDefault();

        $.ajax({
            url: my_ajax_obj.ajax_url,
            method: 'POST',
            data: {
                action: 'submit_form',
                name: $('input[name="name"]').val(),
                security: my_ajax_obj.nonce
            },
            success: function(res) {
                $('#response').html(res);
            }
        });
    });
});
```

**Step 3: PHP handler**

```php
function handle_form_submission() {
    check_ajax_referer('custom_nonce', 'security');

    $name = sanitize_text_field($_POST['name']);
    echo 'Thanks, ' . esc_html($name) . '!';

    wp_die();
}
add_action('wp_ajax_submit_form', 'handle_form_submission');
add_action('wp_ajax_nopriv_submit_form', 'handle_form_submission');
```

---

### REST API Basics

---

#### **1. What is the WordPress REST API?**

The **WordPress REST API** is a feature that allows external applications to **communicate with your WordPress site using HTTP**.

* It supports **GET**, **POST**, **PUT**, **DELETE**, and more.
* Data is sent and received as **JSON**.
* You can access posts, users, comments, and more, or register **custom endpoints**.

**Example:**

```http
GET https://example.com/wp-json/wp/v2/posts
```

REST API allows WordPress to be used as a **headless CMS** or to integrate with React, Vue, mobile apps, and third-party tools.

---

#### **2. What is an endpoint in the REST API?**

An **endpoint** is a specific URL path that the API listens to and responds from.

**Structure:**

```
/wp-json/{namespace}/{route}
```

**Example endpoints:**

* `/wp-json/wp/v2/posts` → retrieves posts
* `/wp-json/wp/v2/pages` → retrieves pages

You can create **custom endpoints** like:

```
/wp-json/myplugin/v1/custom-data
```

Each endpoint maps to a specific **callback function** that processes the request and returns a response.

---

#### **3. How do you fetch posts using the REST API?**

You can fetch posts using a **GET request** to the following URL:

```http
GET https://example.com/wp-json/wp/v2/posts
```

To fetch specific fields or filters:

```http
GET https://example.com/wp-json/wp/v2/posts?per_page=5&orderby=date
```

You can use tools like:

* JavaScript `fetch()`
* jQuery `$.ajax()`
* REST API clients like Postman

**Example in JS:**

```javascript
fetch('/wp-json/wp/v2/posts')
  .then(response => response.json())
  .then(data => console.log(data));
```

---

#### **4. How do you register a custom REST API route?**

Use `register_rest_route()` inside the `rest_api_init` action hook.

**Example:**

```php
function myplugin_register_custom_route() {
    register_rest_route('myplugin/v1', '/greeting', array(
        'methods'  => 'GET',
        'callback' => 'myplugin_handle_greeting_request'
    ));
}
add_action('rest_api_init', 'myplugin_register_custom_route');

function myplugin_handle_greeting_request() {
    return array('message' => 'Hello from the custom REST API route!');
}
```

This creates a new route:

```
GET /wp-json/myplugin/v1/greeting
```

---

#### **5. What is `register_rest_route()`?**

`register_rest_route()` is a WordPress function used to **define custom REST API endpoints**.

**Syntax:**

```php
register_rest_route($namespace, $route, $args);
```

* **\$namespace**: Grouping (e.g., `myplugin/v1`)
* **\$route**: Path (e.g., `/data`)
* **\$args**: Array of settings (methods, callback, permissions)

**Example:**

```php
register_rest_route('myplugin/v1', '/data', array(
    'methods' => 'GET',
    'callback' => 'myplugin_get_data'
));
```

---

#### **6. How do you send data using a POST request in the REST API?**

You send a `POST` request to a custom or built-in endpoint with JSON or form data in the body.

**Example (JavaScript with fetch):**

```javascript
fetch('/wp-json/myplugin/v1/save', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'X-WP-Nonce': my_ajax_obj.nonce
  },
  body: JSON.stringify({ name: 'John Doe' })
})
.then(response => response.json())
.then(data => console.log(data));
```

**PHP handler:**

```php
function myplugin_save_data(WP_REST_Request $request) {
    $name = sanitize_text_field($request->get_param('name'));
    return array('message' => 'Saved: ' . $name);
}
```

Always sanitize and validate input in POST endpoints.

---

#### **7. What is `wp_send_json_success()`?**

This function sends a JSON response with a success status and optional data.

**Example:**

```php
function myplugin_return_data() {
    $data = array('message' => 'Everything worked!');
    wp_send_json_success($data);
}
```

**Output:**

```json
{
  "success": true,
  "data": {
    "message": "Everything worked!"
  }
}
```

There’s also `wp_send_json_error()` for errors.

Use these functions when building AJAX or REST responses manually.

---

#### **8. How do you protect REST API routes with nonces?**

Use `check_ajax_referer()` or `wp_verify_nonce()` in your endpoint to ensure the request is secure.

**Step 1: Pass nonce to JS using `wp_localize_script`:**

```php
function enqueue_nonce_script() {
    wp_enqueue_script('my-js', get_template_directory_uri() . '/js/app.js', array('jquery'), null, true);

    wp_localize_script('my-js', 'my_ajax_obj', array(
        'nonce' => wp_create_nonce('wp_rest')
    ));
}
add_action('wp_enqueue_scripts', 'enqueue_nonce_script');
```

**Step 2: Add permission\_callback check:**

```php
function myplugin_check_permission() {
    return current_user_can('edit_posts') && check_ajax_referer('wp_rest', 'X-WP-Nonce', false);
}

function myplugin_secure_route() {
    register_rest_route('myplugin/v1', '/secure-data', array(
        'methods'             => 'POST',
        'callback'            => 'myplugin_handle_secure',
        'permission_callback' => 'myplugin_check_permission'
    ));
}
add_action('rest_api_init', 'myplugin_secure_route');

function myplugin_handle_secure(WP_REST_Request $request) {
    return array('status' => 'OK');
}
```

---

#### **9. What is the difference between GET and POST methods?**

| Feature       | GET                         | POST                             |
| ------------- | --------------------------- | -------------------------------- |
| Purpose       | Retrieve data               | Submit or change data            |
| Data visible? | Yes (in URL)                | No (in request body)             |
| Use cases     | Fetch posts, pages, options | Create user, update settings     |
| REST Example  | `/wp-json/wp/v2/posts`      | `/wp-json/myplugin/v1/save_data` |

Use GET when no side effects are expected (read-only).
Use POST for actions that **modify** server-side data.

---

#### **10. How do you view the REST API base URL for a site?**

The REST API base URL for any WordPress site is:

```
https://yourdomain.com/wp-json/
```

You can test it by visiting:

```
https://yourdomain.com/wp-json/wp/v2/posts
```

This returns a JSON list of blog posts.

You can also explore all registered routes using:

```
https://yourdomain.com/wp-json
```

This is helpful when testing with Postman or inspecting available routes for custom development.

---

