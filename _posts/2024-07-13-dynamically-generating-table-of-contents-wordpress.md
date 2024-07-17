---
layout: post
title:  Dynamically Generating a Table of Contents in WordPress
meta-description: Learn how to enhance your WordPress site's user experience by dynamically generating a table of contents. This guide provides step-by-step instructions on adding unique IDs to headings and creating an accessible navigation structure.
tags:
  - WordPress
---

When managing content-rich websites, especially educational or documentation sites, a table of contents (TOC) can significantly enhance user navigation and accessibility. In WordPress, while several plugins offer TOC functionality, they might not always align perfectly with your site's specific design or functionality needs. In this blog post, we'll explore a custom implementation to dynamically generate a table of contents and add unique IDs to `h2` tags on specific page templates.

#### The Requirement
The requirement was to implement a dynamic table of contents for specific WordPress page templates. Each `h2` heading needed a unique ID that reflects the text content, converted into a URL-friendly format (slug). This TOC should be automatically injected into designated areas of the page, enhancing navigation without altering the content's structure or presentation.

#### Sample Content
Here's a look at a typical structure of content you might find on a page utilizing this feature:

```html
<h2>Welcome to Our Services</h2>
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin nibh augue, suscipit a, scelerisque sed, lacinia in, mi. Cras vel lorem.</p>

<h2>Features and Benefits</h2>
<p>Etiam pellentesque aliquet tellus. Phasellus pharetra nulla ac diam. Quisque semper justo at risus. Donec venenatis, turpis vel hendrerit interdum.</p>

<h2>Contact Us</h2>
<p>Duis auctor in purus in aliquet. Curabitur auctor, eros aliquet scelerisque luctus, quam nulla ultricies lorem, non euismod arcu ante quis massa.</p>
```

#### Step-by-Step Implementation

##### 1. Adding Unique IDs to all `h2` Tags
We use a PHP function to parse the post content and inject unique IDs. This function checks if the content belongs to a specific template and then processes the headings accordingly.

**PHP Code:**
```php
function add_unique_ids_to_h2($content) {
    if (is_page_template('template-sidebar-toc.php')) {
        $dom = new DOMDocument();
        @$dom->loadHTML('<div>' . mb_convert_encoding($content, 'HTML-ENTITIES', 'UTF-8') . '</div>', LIBXML_HTML_NOIMPLIED | LIBXML_HTML_NODEFDTD);
        $wrapper = $dom->getElementsByTagName('div')->item(0);
        $headers = $wrapper->getElementsByTagName('h2');
        foreach ($headers as $header) {
            $text = trim($header->textContent);
            $slug = strtolower(preg_replace('/[^A-Za-z0-9-]+/', '-', $text));
            $header->setAttribute('id', $slug);
        }
        $content = '';
        foreach ($wrapper->childNodes as $child) {
            $content .= $dom->saveHTML($child);
        }
        return $content;
    }
    return $content;
}
add_filter('the_content', 'add_unique_ids_to_h2');
```

##### 2. Dynamically Generating the TOC
The JavaScript snippet is added to the footer and it constructs the TOC based on the `h2` tags present.

**JavaScript Code:**
```javascript
function add_toc_script() {
    if (is_page_template('template-sidebar-toc.php')) {
        ?>
        <script>
        document.addEventListener("DOMContentLoaded", function() {
            const headers = document.querySelectorAll('h2[id]');
            let tocHTML = '<div id="table-of-contents"><ul>';
            headers.forEach(function(header) {
                tocHTML += `<li><a href="#${header.id}">${header.textContent}</a></li>`;
            });
            tocHTML += '</ul></div>';
            const postContent = document.querySelector('.toc-index');
            if (postContent) {
                postContent.insertAdjacentHTML('afterbegin', tocHTML);
            }
        });
        </script>
        <?php
    }
}
add_action('wp_footer', 'add_toc_script', 999);
```

The above code will insert a TOC on the element with `toc-index` class.

This custom approach allows for greater flexibility and integration with specific page layouts or templates, ensuring that the table of contents aligns perfectly with the design and functionality needs of your WordPress site. By using native WordPress hooks and a bit of JavaScript, we can enhance the user experience without relying on additional plugins.
