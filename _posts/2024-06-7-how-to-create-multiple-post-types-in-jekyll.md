---
layout: post
title:  How to Create Multiple Post Types in Jekyll for Enhanced Content Management
description: Learn how to set up multiple post types in Jekyll to manage diverse content effectively. Step-by-step guide included for blogs, portfolios, and more.
tags:
  - jekyll
---

Jekyll is a powerful static site generator, perfect for blogging and other web content. One of its strengths is the ability to handle multiple post types, making it ideal for diverse content needs such as blogs, portfolios, and documentation.

### Step-by-Step Guide to Multiple Post Types in Jekyll

#### 1. **Create Collection Directory**
Start by creating a new directory in your Jekyll project for each content type. The directory name should begin with an underscore (`_`). For stories, I have created a directory named `_stories`.

#### 2. **Update Configuration**
Update your `_config.yml` file to define the new collection. Add a `collections` section if it doesn't exist, and include your new collection. Set `output: true` if you want each item to be a standalone page.

```yaml
collections:
  stories:
    output: true
```

#### 3. **Create Layouts**
Create a custom layout for your new post type. This can be done by adding a new HTML file in the `_layouts` directory. For example, create a `story.html` file:

{% raw %}
    ---
    layout: default
    ---

    <h1>{{ title }}</h1>
    {{ content }}
{% endraw %}


#### 4. **Create Content Pages**
Within your new collection directory (`_stories`), add individual markdown files for each post. Each file should have appropriate front matter:

```yaml
---
layout: story
title: "Story Title"
description: "Brief description of the story."
---

Content of the story goes here.
```

#### 5. **Index Page**
To link all items in your collection, create an index page. This can be a new HTML file in the site root or within a specific directory. I like the index page URL look like `example.com/stories/`. So I have created a directory named as `stories` & put my `index.md` file in that directory. Use a loop to iterate through the collection items:

{% raw %}
    {% for item in site.stories %}
      <h2>{{ item.title }}</h2>
      <p>{{ item.description }}</p>
      <a href="{{ item.url }}">Read More</a>
    {% endfor %}
{% endraw %}

### Conclusion
Implementing multiple post types in Jekyll allows for a well-organized and versatile content structure. Whether you're adding blogs, portfolios, or documentation, this method ensures your site remains dynamic and user-friendly.
