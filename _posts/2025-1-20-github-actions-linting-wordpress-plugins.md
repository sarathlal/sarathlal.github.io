---
layout: post
title:  Automating Code Linting with GitHub Actions for WordPress Plugins
description: Learn how to automate code linting for WordPress plugins using GitHub Actions. Set up workflows to lint PHP, JavaScript, and CSS files before merging feature branches into the main branch.
tags:
  - Code Quality
  - Code Standard
  - CI / CD Integrations
  - GitHub Actions
---

In the <a href="{{site.baseurl}}/linting-wordpress-plugin-with-composer/">previous post</a>, we discussed setting up PHP, JavaScript, and CSS linting for a WordPress plugin using Composer. Now, let's take it a step further by automating the linting process with GitHub Actions. This ensures that our code is always reviewed for quality before merging feature branches into the main branch.

---

## Why Use GitHub Actions for Linting?

By using GitHub Actions, we can:

- **Automate Linting**: Ensure our code follows defined standards with every pull request.
- **Prevent Errors Early**: Catch issues before they reach the main branch.
- **Streamline Workflow**: Save time and maintain consistency across our team.
- **Enforce Quality**: Integrate with branch protection rules to block merges if linting fails.

---

## Setting Up GitHub Actions for Linting

### Step 1: Create a GitHub Actions Workflow File

In the root of our repository, create a directory named `.github/workflows`. Inside this directory, create a file named `lint.yml`.

### Step 2: Define the Workflow

Paste the following YAML configuration into the `lint.yml` file:

```yaml
name: Lint Code

on:
  pull_request:
    branches:
      - main
      - develop

jobs:
  lint:
    name: Lint Code
    runs-on: ubuntu-latest

    steps:
      # Step 1: Checkout the code
      - name: Checkout Code
        uses: actions/checkout@v3

      # Step 2: Set up PHP environment
      - name: Set up PHP
        uses: shivammathur/setup-php@v2
        with:
          php-version: 8.0
          extensions: mbstring
          tools: composer

      # Step 3: Install Composer dependencies
      - name: Install Composer Dependencies
        run: composer install

      # Step 4: Set up Node.js environment
      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 16

      # Step 5: Install NPM dependencies
      - name: Install NPM Dependencies
        run: npm install

      # Step 6: Lint PHP files
      - name: Lint PHP Files
        run: composer run lint:php

      # Step 7: Lint JavaScript files
      - name: Lint JavaScript Files
        run: composer run lint:js

      # Step 8: Lint CSS files
      - name: Lint CSS Files
        run: composer run lint:css
```

---

## How the Workflow Works

1. **Triggers**: The workflow runs automatically when a pull request targets the `main` or `develop` branches.
2. **Checkout Code**: The `actions/checkout` action retrieves our repository’s code.
3. **PHP Setup**: The `shivammathur/setup-php` action sets up PHP 8.0, installs Composer, and ensures PHP extensions like `mbstring` are available.
4. **Node.js Setup**: The `actions/setup-node` action installs Node.js version 16 to handle JavaScript and CSS linting.
5. **Dependency Installation**:
   - Composer dependencies (for PHP linting) are installed with `composer install`.
   - NPM dependencies (for JavaScript and CSS linting) are installed with `npm install`.
6. **Linting Commands**: The workflow executes the Composer scripts for linting PHP, JavaScript, and CSS.

---

## Enforcing Quality with Branch Protection Rules

To ensure all pull requests are linted before merging, we can enable branch protection rules:

1. Navigate to **Settings** > **Branches** in our GitHub repository.
2. Click **Add Rule** and set it for the `main` or `develop` branch.
3. Enable **Require status checks to pass before merging**.
4. Select **Lint Code** as a required check.
5. Save the rule.

This ensures that a pull request cannot be merged if linting fails.

---

## Optimizing the Workflow

### Caching Dependencies
To speed up the workflow, we can cache Composer and NPM dependencies:


{% raw %}
      # Cache Composer Dependencies
      - name: Cache Composer Dependencies
        uses: actions/cache@v3
        with:
          path: vendor
          key: ${{ runner.os }}-composer-${{ hashFiles('composer.lock') }}
          restore-keys: ${{ runner.os }}-composer-

      # Cache NPM Dependencies
      - name: Cache NPM Dependencies
        uses: actions/cache@v3
        with:
          path: ~/.npm
          key: ${{ runner.os }}-node-${{ hashFiles('package-lock.json') }}
          restore-keys: ${{ runner.os }}-node-
{% endraw %}

### Running Fixers
If we want to automatically fix issues (e.g., during a specific branch or manually triggered workflow), we can add an additional job:

```yaml
  fix:
    name: Fix Code
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v3

      - name: Set up PHP
        uses: shivammathur/setup-php@v2
        with:
          php-version: 8.0
          extensions: mbstring
          tools: composer

      - name: Install Composer Dependencies
        run: composer install

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 16

      - name: Install NPM Dependencies
        run: npm install

      - name: Fix PHP Files
        run: composer run fix:php

      - name: Fix JavaScript Files
        run: composer run fix:js

      - name: Fix CSS Files
        run: composer run fix:css
```

### Notifications
We can use the `actions/github-script` action to leave comments on pull requests if linting fails:

```yaml
      - name: Post Comment on Failure
        if: failure()
        uses: actions/github-script@v6
        with:
          script: |
            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: `Linting failed. Please fix the issues and push the changes.`
            });
```

---

By integrating GitHub Actions into our workflow, we can ensure that code linting becomes an automated and mandatory step before merging any changes into the main branch. This not only saves time but also enforces consistent coding standards across our WordPress plugins.
