---
layout: post
title:  My 28-Day Plan to Master Modern WordPress Development Using AI Tools
description: Learn Gutenberg, React, Full Site Editing, and modern plugin development in just 28 days. This complete WordPress learning roadmap includes daily prompts, real projects, and AI tool-guided tasks for experienced developers ready to upgrade their skills.
tags:
  - WordPress
  - Modern WordPress Development
  - Block development
  - Full Site Editing
  - Gutenberg
---

WordPress has changed a lot over the years. It’s no longer just about PHP templates and shortcodes. With the introduction of Gutenberg, block themes, Full Site Editing (FSE), and React, the way we build WordPress sites has evolved. And if you’ve been working with WordPress for a long time like I have, you’ve probably felt the gap growing between the old way of doing things and what’s considered modern today.

I’ve been a WordPress developer for over 11 years. I’m comfortable building custom plugins, classic themes, and WooCommerce setups. But I realized I was missing some of the newer skills like block development, theme.json, Full Site Editing, and especially React.

So I decided to do something about it.

I created a 28-day learning plan to help developers like me get up to speed with everything modern in WordPress. I used AI tools every day as my learning assistant. Each day, I focused on a small part of the modern WordPress stack, learned the theory, and applied it by building something practical.

If you’re trying to level up your WordPress skills and want a structured way to learn Gutenberg, React, FSE, and more, this plan is for you.

---

## What You’ll Learn

- Gutenberg block development (static and dynamic)
- React for WordPress (JSX, Hooks, wp.data)
- Full Site Editing (FSE) and block theme creation
- theme.json for global styles and layout control
- WooCommerce block integration
- Testing Gutenberg blocks using Jest
- Plugin architecture, performance, and packaging

---

## How to Use This Roadmap

This blog post contains a complete 4-week plan, broken down into daily tasks. Each day includes clear prompts you can use directly with an AI tool, practical coding exercises, and instructions for when to upload your project code to continue building.

I’m planning to start a new chat every day. At the beginning of each day, I’ll first share my learning requirement as a prompt to set the proper context.

Here’s the base prompt I’ll be using at the start of each day:

> Hi! I’m starting today’s learning session and I’m new to this topic, so I’d like to learn it in depth. Please explain things like you’re teaching a junior developer who’s just getting started. Keep the explanations clear and simple. When you share code, walk me through it step by step and explain how and why it works. If you create any new files or folders, let me know why you chose that name and where you placed it. And if something is important or often misunderstood, feel free to go deeper, even if I don’t ask.

Only after setting the learning context, I will start asking the daily prompts.

This method ensures a proper flow, keeps the AI focused on the right learning style, and helps achieve maximum depth of understanding.

---

## Week 1: Gutenberg Block Development and React Fundamentals

**Goal:** Understand the Gutenberg editor, create static blocks, and learn foundational React to prepare for advanced block development.

---

### Day 1: Introduction to Gutenberg and Block Development  

**Prompt 1:**  
What is Gutenberg and how is it different from the classic WordPress editor? Why is it important for modern WordPress development?

**Prompt 2:**  
What are blocks in Gutenberg? Explain how block attributes, `InnerBlocks`, and custom block types work.

**Prompt 3:**  
Help me set up a development environment using `@wordpress/scripts` and scaffold my first custom block plugin.

**Prompt 4:**  
Show me how to register a block using `block.json`, and explain how the `edit` and `save` functions work in a simple “Hello Block”.

**Prompt 5:**  
Let’s create an “Info Box” block that has a heading and a paragraph. Show me how to make the text editable using block attributes.

---

### Day 2: Using Attributes and Inspector Controls  
*Continuation optional — you can reuse the block from Day 1.*

**If continuing, say:**  
> I’ve uploaded the block plugin I started yesterday. Please use it as a base to continue building.

**Prompt 1:**  
What are block attributes, and how are they stored and passed between the editor and the frontend?

**Prompt 2:**  
Help me add `InspectorControls` to the sidebar with a toggle or color selector.

**Prompt 3:**  
Let’s build a simple “Pricing Table” block with 3 pricing columns (title, price, features).

**Prompt 4:**  
How can I make this block fully editable using attributes?

**Prompt 5:**  
How do I style this block using SCSS or inline styles, and apply styles in both the editor and frontend?

---

### Day 3: Introduction to React – JSX and Components  
*Start fresh — no upload needed.*

**Prompt 1:**  
What is JSX in React, and how is it different from HTML?

**Prompt 2:**  
How do I create a functional component using props and state? Let’s build a simple counter.

**Prompt 3:**  
Help me build a small app using components — a todo list with add/remove functionality.

**Prompt 4:**  
Show me how to pass data between components using props.

**Prompt 5:**  
How do I use array `.map()` and conditional rendering in React?

---

### Day 4: React – Forms, State, and Events  
*Continue learning React — no upload needed.*

**Prompt 1:**  
What is `useState` and how is it used in forms? Show me how to create controlled inputs in React.

**Prompt 2:**  
Let’s build a contact form with name, email, and message fields. Capture and manage input values.

**Prompt 3:**  
How do I handle form submission and display a success message?

**Prompt 4:**  
Help me add simple validation to check if fields are empty.

**Prompt 5:**  
How can I turn this form into a reusable component?

---

### Day 5: React – useEffect and Component Lifecycle  
*Still working in standalone React — no upload needed.*

**Prompt 1:**  
What is `useEffect`, and how does it compare to class-based lifecycle methods like `componentDidMount`?

**Prompt 2:**  
Help me build a component that fetches data using `useEffect` (e.g. from a public API or mock JSON).

**Prompt 3:**  
How do I handle cleanup with `useEffect`, like cancelling timers or aborting fetches?

**Prompt 4:**  
Can I use multiple `useEffect` hooks in the same component? How are they handled?

**Prompt 5:**  
How do I conditionally run `useEffect` when certain values change?

---

### Day 6: Build a Card Block with Gutenberg and React  
*New plugin project. You’ll build a custom block with editor UI and styling.*

**Prompt 1:**  
I want to build a “Card Block” with a title, image, and description. Help me plan the attributes and block layout.

**Prompt 2:**  
How can I let users upload an image and enter text in the block editor?

**Prompt 3:**  
Help me add InspectorControls to allow users to change the card’s background color.

**Prompt 4:**  
Guide me through building the `save()` function and applying styling for the frontend.

**Prompt 5:**  
How do I organize the block folder structure using `@wordpress/scripts`?

---

### Day 7: Build a Team Member Block (Mini Project)  
**Continuation recommended — reuse the card block structure. Upload ZIP from Day 6.**

**Before starting, say:**  
> I’ve uploaded my plugin from Day 6. Please extract the code and help me extend it to create a Team Member block.

**Prompt 1:**  
I want to build a Team Member block with name, photo, role, and social media links. Help me plan the attributes.

**Prompt 2:**  
Let’s build the editor UI with editable fields, media upload, and input validation.

**Prompt 3:**  
Add InspectorControls for layout options (e.g. alignment, background color).

**Prompt 4:**  
Help me polish the frontend view with clean styling and good structure.

**Prompt 5:**  
How do I package this block plugin with a proper `readme.txt` and structure for reuse or GitHub?

---

## Week 2: Dynamic Blocks, WordPress Data, and Dev Tools
 
**Goal:** Create dynamic Gutenberg blocks, integrate REST and WooCommerce APIs, explore WordPress data handling, and understand dev tools.

---

### Day 8: Introduction to Dynamic Blocks  
*Start fresh – no upload required.*

**Prompt 1:**  
What are dynamic blocks in Gutenberg? When should I use dynamic rendering instead of static `save()`?

**Prompt 2:**  
Show me how to create a simple dynamic block using `ServerSideRender` that displays the current date and time.

**Prompt 3:**  
How do I register and render dynamic block output using `render_callback`?

**Prompt 4:**  
How do block attributes work in a dynamic block, and how can I access them in PHP?

**Prompt 5:**  
How do I test and debug a dynamic block?

---

### Day 9: REST API and wp.data  
*Start fresh – no upload required.*

**Prompt 1:**  
I want to create a block that shows the latest blog posts. How can I fetch data using the WordPress REST API?

**Prompt 2:**  
Help me build a block using `useEffect` and `fetch()` to display post titles and excerpts.

**Prompt 3:**  
What’s the difference between using REST directly and using `wp.data` with `useSelect`?

**Prompt 4:**  
Show me how to refactor the block to use `useSelect` to pull posts from the WordPress data store.

**Prompt 5:**  
How do I add a setting in InspectorControls to choose how many posts to display?

---

### Day 10: wp.data – Select & Dispatch  
**Optional continuation:**  
If you’re building on a previous block, upload your ZIP file. Otherwise, start fresh.

**Before starting, say:**  
> I’m continuing from yesterday. I’ve uploaded my block plugin ZIP file. Please extract and continue from the existing code.

**Prompt 1:**  
What are `useSelect` and `useDispatch` in Gutenberg? How do they help manage post data?

**Prompt 2:**  
Show me how to read post meta using `useSelect`.

**Prompt 3:**  
How can I update post meta using `useDispatch` with `core/editor`?

**Prompt 4:**  
Let’s build a UI inside the block to modify post meta values directly.

**Prompt 5:**  
How do I save and validate post meta changes in the block editor?

---

### Day 11: WooCommerce Product Grid Block  
**Recommended continuation:**  
Upload yesterday’s plugin if you’re building on a meta block, or start a new one for WooCommerce.

**Before starting, say:**  
> I’ve uploaded my plugin ZIP file. Please extract and build a WooCommerce product block inside it, or reuse the structure if appropriate.

**Prompt 1:**  
How can I fetch WooCommerce product data using the REST API?

**Prompt 2:**  
Guide me to build a product grid block that shows image, title, price, and "Add to Cart" button.

**Prompt 3:**  
How do I add a dropdown to filter products by category?

**Prompt 4:**  
How can I handle loading and error states while fetching product data?

**Prompt 5:**  
What are best practices for working with WooCommerce blocks?

---

### Day 12: Testing Blocks with Jest  
**Continuation required:**  
Upload the plugin from Day 11 or any earlier block you want to test.

**Before starting, say:**  
> I’ve uploaded my plugin ZIP file. Please extract it and help me set up tests for the components inside this plugin.

**Prompt 1:**  
What is Jest and how is it used to test WordPress Gutenberg blocks?

**Prompt 2:**  
How do I set up Jest for a block plugin using `@wordpress/scripts`?

**Prompt 3:**  
Show me how to write a unit test for a utility function in my plugin.

**Prompt 4:**  
How do I test a React component from my block and mock its props?

**Prompt 5:**  
Where should I place my tests inside the plugin structure, and how do I run them?

---

### Day 13: Webpack, Babel, and Build Tools  
*Start fresh – no upload required.*

**Prompt 1:**  
What is included in `@wordpress/scripts`, and how does it simplify the block development workflow?

**Prompt 2:**  
What roles do Webpack, Babel, and PostCSS play when I build a block plugin?

**Prompt 3:**  
How can I override `@wordpress/scripts` and define my own Webpack configuration?

**Prompt 4:**  
Show me how to create a manual build setup with SCSS, Babel, and JSX support.

**Prompt 5:**  
When is it better to use custom tooling vs the default WordPress script setup?

---

### Day 14: Project – Build a FAQ Block Plugin  
**New plugin recommended. You may upload an earlier block’s ZIP to reuse structure.**

**Before starting, say:**  
> I’ve uploaded the plugin ZIP I want to build the FAQ Block in, or reuse the block structure. Please extract and use this as a base.

**Prompt 1:**  
I want to build a reusable FAQ block. What attributes and structure should I use?

**Prompt 2:**  
Can I use `InnerBlocks` or a repeater structure for multiple question-answer pairs?

**Prompt 3:**  
Help me build the toggle behavior in React so answers show/hide when clicked.

**Prompt 4:**  
How can I style this block to look clean and collapsible on the frontend?

**Prompt 5:**  
Help me package this as a standalone plugin with a readme and assets folder for distribution or GitHub.

---

## Week 3: Full Site Editing and Block Themes
 
**Goal:** Learn the structure and power of Full Site Editing, build a block theme from scratch, and convert classic templates to modern equivalents.

---

### Day 15: Intro to FSE and Block Themes  
*Start fresh – no upload needed. You’ll create a new theme folder today.*

**Prompt 1:**  
What is Full Site Editing (FSE)? How does it change the way themes work compared to classic PHP-based themes?

**Prompt 2:**  
What is the basic folder structure of a block theme? Explain the role of `theme.json`, `templates`, and `parts`.

**Prompt 3:**  
Help me scaffold a new block theme folder with `style.css`, `theme.json`, and basic templates (`index.html`, `home.html`).

**Prompt 4:**  
How do I register the theme properly in `style.css`, and how do I test it in WordPress?

**Prompt 5:**  
Help me create a minimal homepage with a heading, image, and paragraph using only blocks.

---

### Day 16: Header, Footer, and Templates  
**Continuation recommended – upload your theme folder from Day 15.**

**Before starting, say:**  
> I’ve uploaded my block theme folder from yesterday. Please extract it and help me continue building the theme today.

**Prompt 1:**  
How do I create reusable template parts like `header.html` and `footer.html`? What blocks should go inside?

**Prompt 2:**  
Help me insert the header and footer template parts into the main templates like `index.html` and `home.html`.

**Prompt 3:**  
Guide me through building `page.html` and `single.html` templates that include post content and metadata.

**Prompt 4:**  
How can I structure the templates to work with the template hierarchy in FSE?

**Prompt 5:**  
Let’s test these templates in WordPress and ensure they display correctly.

---

### Day 17: Deep Dive into theme.json  
**Continuation required – upload your theme folder again.**

**Before starting, say:**  
> I’ve uploaded my block theme folder. Please use the existing structure and help me enhance it using `theme.json`.

**Prompt 1:**  
What is `theme.json` and how does it control global styles and settings?

**Prompt 2:**  
Help me define custom color palettes, font sizes, spacing units, and layout options in `theme.json`.

**Prompt 3:**  
How can I disable default block features like drop caps, custom spacing, or font sizes?

**Prompt 4:**  
Let’s test global styles inside editor blocks and verify that they reflect properly in both the editor and frontend.

**Prompt 5:**  
How do I organize and document `theme.json` settings for long-term use?

---

### Day 18: Archive and Special Templates  
**Continuation required – upload your theme folder.**

**Before starting, say:**  
> I’ve uploaded my theme again. I want to add archive, 404, and search result templates today.

**Prompt 1:**  
How do I create archive templates like `archive.html`, `category.html`, and `author.html`?

**Prompt 2:**  
Show me how to design a basic 404 page using a custom template and blocks.

**Prompt 3:**  
Help me build a `search.html` template that displays results with excerpts and featured images.

**Prompt 4:**  
How does the FSE template hierarchy determine which template is used on different pages?

**Prompt 5:**  
How can I preview and test each of these templates inside WordPress?

---

### Day 19: Navigation, Query Loops, and Dynamic Content  
**Continuation required – upload your theme folder.**

**Before starting, say:**  
> I’ve uploaded the same block theme folder. I want to add navigation and dynamic content blocks.

**Prompt 1:**  
How do I build a dynamic Navigation Block with nested items and styling?

**Prompt 2:**  
Help me use the Query Loop block to show recent posts on the homepage or archive templates.

**Prompt 3:**  
How can I display featured images, post excerpts, dates, and authors inside a query loop?

**Prompt 4:**  
How do I create sidebars or secondary columns in block themes using layouts or template parts?

**Prompt 5:**  
Let’s test this on the homepage and archives to ensure everything updates dynamically.

---

### Day 20: Converting a Classic Theme to Block Theme  
**Start with any classic theme ZIP or description of your current theme.**

**Before starting, say:**  
> I want to convert a classic theme to a block theme. Here's a ZIP or summary of the classic template structure I want to replicate.

**Prompt 1:**  
How do I identify which templates and functions from a classic theme map to FSE equivalents?

**Prompt 2:**  
Show me how to replace `get_header()`, `get_footer()`, `the_content()` with block-based templates.

**Prompt 3:**  
Help me recreate the layout of the classic theme’s homepage using only blocks.

**Prompt 4:**  
What’s the best way to match the old design using `theme.json` styles?

**Prompt 5:**  
How can I test the FSE version side by side with the classic version and ensure consistency?

---

### Day 21: Polish and Package Your Block Theme  
**Continuation required – upload your full theme folder.**

**Before starting, say:**  
> I’ve uploaded my complete block theme. Please help me polish and prepare it for public release.

**Prompt 1:**  
How do I clean up template files, remove unused parts, and structure the theme for release?

**Prompt 2:**  
Help me improve responsive layout and spacing using block layout settings or `theme.json`.

**Prompt 3:**  
How can I test my theme using WordPress Theme Unit Test data?

**Prompt 4:**  
Show me how to write a `readme.txt`, include a screenshot, and prepare the theme for GitHub or wp.org.

**Prompt 5:**  
Suggest final QA steps and future improvements for this theme.

---

## Week 4: Real-World Projects, WooCommerce, and Final Release

**Goal:** Build a complete plugin, integrate Gutenberg with WooCommerce, follow best practices, and prepare for production release.

---

### Day 22: Start a Real-World Plugin Project  
*Start a new plugin today. You'll continue this for multiple days.*

**Before starting, say:**  
> I’m starting a new Gutenberg plugin project today. I’ll be uploading this plugin’s ZIP in the next few days as I continue. Please help me plan and scaffold the structure.

**Prompt 1:**  
Help me choose a real-world Gutenberg plugin idea — something like a Recipe Block, Testimonial Block, or Event Block.

**Prompt 2:**  
How should I structure the plugin folders for a scalable setup (block folder, `block.json`, build config, etc.)?

**Prompt 3:**  
Help me initialize the plugin using `@wordpress/scripts` and create a base block.

**Prompt 4:**  
Let’s register the plugin and block correctly. Show me the PHP and JS required.

**Prompt 5:**  
Can you help me define initial block attributes and save a minimal version?

---

### Day 23: Build the Plugin’s UI  
**Continuation required – upload your plugin ZIP from Day 22.**

**Before starting, say:**  
> I’ve uploaded the plugin I started yesterday. Please extract the code and help me continue working on the block UI.

**Prompt 1:**  
Guide me through building a React-based UI inside the block editor using text inputs and media upload.

**Prompt 2:**  
How do I use `useState` and block attributes together for inputs?

**Prompt 3:**  
Let’s add styling to the editor view with SCSS or utility classes.

**Prompt 4:**  
Help me implement InspectorControls for block options like alignment, colors, or toggles.

**Prompt 5:**  
How do I save all the editor data to render it cleanly in the frontend?

---

### Day 24: Add Advanced Controls and Variations  
**Continuation required – upload the updated plugin ZIP from Day 23.**

**Before starting, say:**  
> I’ve uploaded the plugin with the block I started. Please help me extend it with advanced controls and variations.

**Prompt 1:**  
Show me how to add toggle switches, sliders, dropdowns, and color pickers using block controls and InspectorControls.

**Prompt 2:**  
Can I create style variations or block styles for my block (e.g. alternate layout or color scheme)?

**Prompt 3:**  
How do I manage conditional rendering of UI in the editor based on selected settings?

**Prompt 4:**  
Let’s validate block attributes and sanitize any user-generated content.

**Prompt 5:**  
What are good design patterns for managing large blocks with many settings?

---

### Day 25: WooCommerce Integration  
**Start a new block or reuse plugin from earlier. Upload required.**

**Before starting, say:**  
> I want to build a Gutenberg block that integrates with WooCommerce. I’ve uploaded a plugin where I’d like to add the product block. Please help me extend it.

**Prompt 1:**  
How do I fetch WooCommerce products using the REST API in a Gutenberg block?

**Prompt 2:**  
Let’s build a product grid block that displays product name, image, price, and an “Add to Cart” button.

**Prompt 3:**  
How do I add a dropdown to filter products by category?

**Prompt 4:**  
How can I manage loading, empty states, and errors gracefully?

**Prompt 5:**  
Help me optimize the data fetch performance and minimize bundle size.

---

### Day 26: Prepare the Plugin for Production  
**Continuation required – upload the final plugin from Day 25 or earlier.**

**Before starting, say:**  
> I’ve uploaded my plugin. Please help me prepare it for production — optimize, test, and finalize it.

**Prompt 1:**  
How do I add translation support with `__()` and `wp.i18n`?

**Prompt 2:**  
What accessibility practices should I follow (ARIA labels, focus states, keyboard nav)?

**Prompt 3:**  
How do I optimize the final JS and CSS build using `@wordpress/scripts` or Webpack?

**Prompt 4:**  
Help me clean up unused files, add comments, and prepare the file structure for distribution.

**Prompt 5:**  
How should I test my plugin with different themes, block editors, and screen sizes?

---

### Day 27: Finalize and Package Your Plugin  
**Upload final plugin ZIP for polishing.**

**Before starting, say:**  
> I’ve uploaded my final plugin. Please help me package it for public release, including readme, screenshots, and licensing.

**Prompt 1:**  
How do I write a proper `readme.txt` for my plugin with usage, installation, and FAQ?

**Prompt 2:**  
What screenshot sizes and file structure should I follow for WordPress.org or GitHub?

**Prompt 3:**  
Help me include a `license.txt`, versioning in PHP header, and changelog file.

**Prompt 4:**  
What’s the best way to zip and prepare the plugin for upload to the WP plugin repo or GitHub?

**Prompt 5:**  
Help me double-check the code for WordPress coding standards and errors.

---

### Day 28: Final Review and Roadmap  
**Optional upload – you can include your plugin/theme if you want a full code review.**

**Before starting, say:**  
> I’ve uploaded my plugin/theme for final review. Please help me reflect on what I’ve learned and plan my next steps.

**Prompt 1:**  
Let’s review the core concepts I’ve learned this month (Gutenberg, React, FSE, WooCommerce, packaging).

**Prompt 2:**  
What areas should I revisit or deepen to gain more confidence?

**Prompt 3:**  
Help me write a summary of my learning journey — I want to post this on LinkedIn or my blog.

**Prompt 4:**  
Can you help me create a checklist of best practices I should follow for future projects?

---

## Conclusion

After 28 days, I can confidently say that I no longer feel left behind. I now understand how the block editor works, how to build custom blocks with React, how Full Site Editing is changing themes, and how to make everything work together smoothly.

The plan is intense, especially if you're like me and prefer to dive deep into learning every day. But it's worth it. Every day builds on the last. You’ll not only learn modern concepts, you’ll also create real projects like custom blocks, block-based themes, and full-featured plugins.

You can follow this plan exactly, or you can use it as a flexible guide to go at your own pace. It’s built for developers who already know their way around WordPress but want to catch up with everything new.

Let’s rebuild our WordPress skills with the help of AI tools and keep up with the future.

