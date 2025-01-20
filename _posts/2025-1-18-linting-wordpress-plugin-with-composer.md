---
layout: post
title:  Comprehensive Guide to Linting PHP, JavaScript, and CSS in WordPress Plugins Using Composer
description: Streamline your WordPress plugin development with this comprehensive guide to linting PHP, JavaScript, and CSS using Composer. Learn how to integrate PHP_CodeSniffer, ESLint, and Stylelint to maintain clean, error free code.
tags:
  - Best Practices
  - Code Quality
  - Code Standard
  - WordPress Coding Standards
---

Linting is an essential part of modern development practices. It ensures our code adheres to defined standards and avoids common errors. This blog post provides a detailed guide on how to lint PHP, JavaScript, and CSS files in a WordPress plugin using **Composer**.

## Why Linting Matters

- **Code Consistency**: Ensures uniform coding styles.
- **Error Prevention**: Identifies potential bugs early.
- **Improved Collaboration**: Makes code easier to review and maintain.

For WordPress development, adhering to its coding standards ensures better compatibility, readability, and maintainability.

---

## 1. Linting PHP Files

For PHP files, we'll use **PHP\_CodeSniffer** and the **WordPress Coding Standards** (WPCS).

### Step 1: Install PHP\_CodeSniffer and WPCS

In our plugin's root directory, configure Composer to allow the PHPCS plugin and then install the necessary dependencies:

```bash
composer config allow-plugins.dealerdirect/phpcodesniffer-composer-installer true
composer require --dev wp-coding-standards/wpcs:"^3.0"
```

Composer will automatically install the project dependencies and register the rulesets from WordPressCS with PHP\_CodeSniffer.

### Step 2: Verify Installation

Verify that WordPress Coding Standards are registered with PHP\_CodeSniffer:

```bash
vendor/bin/phpcs -i
```

We should see a list of installed coding standards, including WordPress.

### Step 3: Lint PHP Files

To lint all PHP files in our plugin, run:

```bash
vendor/bin/phpcs --standard=WordPress --extensions=php --ignore=vendor,node_modules .
```

### Step 4: Automatically Fix Issues

To fix issues automatically, use **PHP Code Beautifier and Fixer (PHPCBF):**

```bash
vendor/bin/phpcbf --standard=WordPress --extensions=php --ignore=vendor,node_modules .
```

---

## 2. Linting JavaScript Files

For JavaScript files, we'll use **ESLint** with the WordPress configuration.

### Step 1: Install ESLint and WordPress Configuration

Install ESLint and the WordPress ESLint configuration:

```bash
npm install eslint eslint-config-wordpress @eslint/js @eslint/eslintrc --save-dev
```

### Step 2: Create ESLint Configuration File

Create an `eslint.config.mjs` file in Our plugin's root directory:

```javascript
import path from "node:path";
import { fileURLToPath } from "node:url";
import js from "@eslint/js";
import { FlatCompat } from "@eslint/eslintrc";

const __filename = fileURLToPath(import.meta.url);
const __dirname = path.dirname(__filename);
const compat = new FlatCompat({
    baseDirectory: __dirname,
    recommendedConfig: js.configs.recommended,
    allConfig: js.configs.all
});

export default [
    {
        ignores: ["**/vendor/", "**/node_modules/"],
    },
    ...compat.extends("wordpress"),
    {
        rules: {
            "no-console": "warn",
            quotes: ["error", "double"],
        },
    },
];
```

### Step 3: Lint JavaScript Files

To lint all JavaScript files, run:

```bash
npx eslint "**/admin/js/*.js" "**/public/js/*.js"
```

### Step 4: Automatically Fix Issues

To fix issues automatically:

```bash
npx eslint --fix "**/admin/js/*.js" "**/public/js/*.js"
```

---

## 3. Linting CSS Files

For CSS files, we'll use **Stylelint** with the WordPress configuration.

### Step 1: Install Stylelint and WordPress Configuration

Install Stylelint and the WordPress configuration:

```bash
npm install stylelint stylelint-config-wordpress --save-dev
```

### Step 2: Create Stylelint Configuration File

Create a `.stylelintrc.json` file in our plugin's root directory:

```json
{
    "extends": "stylelint-config-wordpress",
    "ignoreFiles": ["**/vendor/**", "**/node_modules/**"]
}
```

### Step 3: Lint CSS Files

To lint all CSS files, run:

```bash
npx stylelint "**/admin/css/*.css" "**/public/css/*.css"
```

### Step 4: Automatically Fix Issues

To fix issues automatically:

```bash
npx stylelint --fix "**/admin/css/*.css" "**/public/css/*.css"
```

---

## 4. Integrating with Composer

To simplify linting and fixing, we can add scripts to our `composer.json` file:

### Add Scripts to `composer.json`

```json
{
    "scripts": {
        "lint:php": "vendor/bin/phpcs --standard=WordPress --extensions=php --ignore=vendor,node_modules .",
        "fix:php": "vendor/bin/phpcbf --standard=WordPress --extensions=php --ignore=vendor,node_modules .",
        "lint:js": "npx eslint \"**/admin/js/*.js\" \"**/public/js/*.js\"",
        "fix:js": "npx eslint --fix \"**/admin/js/*.js\" \"**/public/js/*.js\"",
        "lint:css": "npx stylelint \"**/admin/css/*.css\" \"**/public/css/*.css\"",
        "fix:css": "npx stylelint --fix \"**/admin/css/*.css\" \"**/public/css/*.css\"",
        "lint": ["@lint:php", "@lint:js", "@lint:css"],
        "fix": ["@fix:php", "@fix:js", "@fix:css"]
    }
}
```
Here is my final `composer.json` file.

```json
{
    "require-dev": {
        "wp-coding-standards/wpcs": "^3.0"
    },
    "config": {
        "allow-plugins": {
            "dealerdirect/phpcodesniffer-composer-installer": true
        }
    },
    "scripts": {
        "lint:php": "vendor/bin/phpcs --standard=WordPress --extensions=php --ignore=vendor,node_modules .",
        "fix:php": "vendor/bin/phpcbf --standard=WordPress --extensions=php --ignore=vendor,node_modules .",
        "lint:js": "npx eslint \"**/admin/js/*.js\" \"**/public/js/*.js\"",
        "fix:js": "npx eslint --fix \"**/admin/js/*.js\" \"**/public/js/*.js\"",
        "lint:css": "npx stylelint \"**/admin/css/*.css\" \"**/public/css/*.css\"",
        "fix:css": "npx stylelint --fix \"**/admin/css/*.css\" \"**/public/css/*.css\"",
        "lint": ["@lint:php", "@lint:js", "@lint:css"],
        "fix": ["@fix:php", "@fix:js", "@fix:css"]
    }
}
```

### Usage

- Lint PHP:
  ```bash
  composer run lint:php
  ```
- Fix PHP:
  ```bash
  composer run fix:php
  ```
- Lint JavaScript:
  ```bash
  composer run lint:js
  ```
- Fix JavaScript:
  ```bash
  composer run fix:js
  ```
- Lint CSS:
  ```bash
  composer run lint:css
  ```
- Fix CSS:
  ```bash
  composer run fix:css
  ```
- Lint Everything:
  ```bash
  composer run lint
  ```
- Fix Everything:
  ```bash
  composer run fix
  ```

---

## 5. Optional Enhancements

### Pre-commit Hooks with Husky

To ensure code is linted before commits, install Husky:

```bash
npm install husky --save-dev
npx husky install
npx husky add .husky/pre-commit "composer run lint"
```

### Continuous Integration

Integrate linting into our CI/CD pipeline using tools like GitHub Actions or GitLab CI/CD.

---

By setting up PHP\_CodeSniffer, ESLint, and Stylelint with Composer, we can create a streamlined workflow for linting and fixing code in our WordPress plugin. This ensures our plugin adheres to WordPress coding standards and maintains high-quality code across all files.


