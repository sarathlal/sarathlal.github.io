---
layout: post
title:  A Guide to Configuring JavaScript and SCSS Paths in WordPress Plugins with @wordpress/scripts
description: Learn how to configure JavaScript paths in WordPress plugins using @wordpress/scripts. Explore practical use cases, folder structures, and npm configurations to optimize your plugin's JavaScript development workflow.
tags:
  - WordPress
---

Every WordPress plugin comes with unique requirements, which often necessitate distinct file structures and build processes. As a developer working on a plugin for the first time with `@wordpress/scripts`, I explored various approaches to manage JavaScript and SCSS files efficiently. Below, I’ve documented different use cases, folder structures, and configuration setups to help developers leverage `@wordpress/scripts` effectively in WordPress plugin development.

---

## Use Case 1: Default Setup with `@wordpress/scripts` for JS and SCSS
### Description
This is the simplest setup where you have a single `src` folder for JavaScript and SCSS files, and the output is compiled into a `dist` folder.

### Folder Structure
```
project/
    src/
        index.js
        styles.scss
    dist/
package.json
```

### Example `index.js`
```javascript
import './styles.scss';
console.log('Scripts and styles bundled!');
```

### `package.json` Configuration
```json
{
    "devDependencies": {
        "@wordpress/scripts": "^30.7.0"
    },
    "scripts": {
        "build": "wp-scripts build src/index.js --output-path=dist",
        "start": "wp-scripts start src/index.js --output-path=dist"
    }
}
```

---

## Use Case 2: Separate Sources for Admin and Frontend (JS and SCSS)
### Description
When the plugin requires separate JavaScript and SCSS files for the admin and frontend, each with its own source and output folder, you can use multiple build scripts.

### Folder Structure
```
admin/
    js/
        src/
            index.js
    css/
        src/
            styles.scss
    dist/

public/
    js/
        src/
            index.js
    css/
        src/
            styles.scss
    dist/
package.json
```

### Example `index.js`
For admin:
```javascript
import '../../css/src/styles.scss';
console.log('Admin scripts and styles bundled!');
```

For public:
```javascript
import '../../css/src/styles.scss';
console.log('Public scripts and styles bundled!');
```

### `package.json` Configuration
```json
{
    "devDependencies": {
        "@wordpress/scripts": "^30.7.0"
    },
    "scripts": {
        "build:admin-js": "wp-scripts build admin/js/src/index.js --output-path=admin/dist",
        "build:admin-css": "wp-scripts build admin/css/src/styles.scss --output-path=admin/dist",
        "build:admin": "npm run build:admin-js && npm run build:admin-css",
        "build:public-js": "wp-scripts build public/js/src/index.js --output-path=public/dist",
        "build:public-css": "wp-scripts build public/css/src/styles.scss --output-path=public/dist",
        "build:public": "npm run build:public-js && npm run build:public-css",
        "build": "npm run build:admin && npm run build:public",
        "start:admin-js": "wp-scripts start admin/js/src/index.js --output-path=admin/dist",
        "start:admin-css": "wp-scripts start admin/css/src/styles.scss --output-path=admin/dist",
        "start:admin": "npm run start:admin-js && npm run start:admin-css",
        "start:public-js": "wp-scripts start public/js/src/index.js --output-path=public/dist",
        "start:public-css": "wp-scripts start public/css/src/styles.scss --output-path=public/dist",
        "start:public": "npm run start:public-js && npm run start:public-css",
        "start": "npm run start:admin && npm run start:public"
    }
}
```

---

## Use Case 3: Multiple Files in `src` Bundled into Separate Outputs
### Description
When you have multiple JavaScript and SCSS files in the `src` folder that need to be individually processed and output to the `dist` folder.

### Folder Structure
```
admin/
    js/
        src/
            file1.js
            file2.js
    css/
        src/
            file1.scss
            file2.scss
    dist/

public/
    js/
        src/
            file1.js
            file2.js
    css/
        src/
            file1.scss
            file2.scss
    dist/
package.json
```

### Example `package.json` Configuration
```json
{
    "devDependencies": {
        "@wordpress/scripts": "^30.7.0"
    },
    "scripts": {
        "build:admin-js": "wp-scripts build admin/js/src/file1.js admin/js/src/file2.js --output-path=admin/dist",
        "build:admin-css": "wp-scripts build admin/css/src/file1.scss admin/css/src/file2.scss --output-path=admin/dist",
        "build:admin": "npm run build:admin-js && npm run build:admin-css",
        "build:public-js": "wp-scripts build public/js/src/file1.js public/js/src/file2.js --output-path=public/dist",
        "build:public-css": "wp-scripts build public/css/src/file1.scss public/css/src/file2.scss --output-path=public/dist",
        "build:public": "npm run build:public-js && npm run build:public-css",
        "build": "npm run build:admin && npm run build:public",
        "start:admin-js": "wp-scripts start admin/js/src/file1.js admin/js/src/file2.js --output-path=admin/dist",
        "start:admin-css": "wp-scripts start admin/css/src/file1.scss admin/css/src/file2.scss --output-path=admin/dist",
        "start:admin": "npm run start:admin-js && npm run start:admin-css",
        "start:public-js": "wp-scripts start public/js/src/file1.js public/js/src/file2.js --output-path=public/dist",
        "start:public-css": "wp-scripts start public/css/src/file1.scss public/css/src/file2.scss --output-path=public/dist",
        "start:public": "npm run start:public-js && npm run start:public-css",
        "start": "npm run start:admin && npm run start:public"
    }
}
```

---

## Use Case 4: Multiple Files Bundled into a Single Output
### Description
When you have multiple JavaScript and SCSS files but want all of them bundled into a single output file for both JavaScript and CSS.

### Folder Structure
```
admin/
    js/
        src/
            file1.js
            file2.js
    css/
        src/
            file1.scss
            file2.scss
    dist/

public/
    js/
        src/
            file1.js
            file2.js
    css/
        src/
            file1.scss
            file2.scss
    dist/
package.json
```

### Example `index.js`
For admin:
```javascript
import '../css/src/file1.scss';
import '../css/src/file2.scss';
import './file1';
import './file2';
console.log('Admin scripts and styles bundled into a single file!');
```

For public:
```javascript
import '../css/src/file1.scss';
import '../css/src/file2.scss';
import './file1';
import './file2';
console.log('Public scripts and styles bundled into a single file!');
```

### `package.json` Configuration
```json
{
    "devDependencies": {
        "@wordpress/scripts": "^30.7.0"
    },
    "scripts": {
        "build:admin": "wp-scripts build admin/js/src/index.js --output-path=admin/dist",
        "build:public": "wp-scripts build public/js/src/index.js --output-path=public/dist",
        "build": "npm run build:admin && npm run build:public",
        "start:admin": "wp-scripts start admin/js/src/index.js --output-path=admin/dist",
        "start:public": "wp-scripts start public/js/src/index.js --output-path=public/dist",
        "start": "npm run start:admin && npm run start:public"
    }
}
```

---

## Conclusion
Each of these use cases demonstrates a unique way to configure `@wordpress/scripts` based on your plugin’s requirements. Whether you need a simple setup, separate admin and frontend builds, or bundling multiple files into separate or single outputs, `@wordpress/scripts` provides the flexibility to handle these scenarios effectively.

This exploration reflects my first attempt at using `@wordpress/scripts` in a plugin. I hope this note serves as a guide for others venturing into modern JavaScript and SCSS development in WordPress!

