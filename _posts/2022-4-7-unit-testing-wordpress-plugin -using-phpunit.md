---
title: Unit testing WordPress plugin using PHPUnit
layout: post
tags:
  - WordPress
  - PHPUnit
  - Unit Test
  - CI/CD
---

### Prerequisite

Here is my system stack & supporting tools with version number.

1. LAMP stack (Linux Mint 20.2, Apache 2.4.41, MySql 15.1, PHP 7.4.3)
2. WordPress (5.9)
2. WP-CLI (2.5.0)
3. WordPress Plugin to be tested
4. Composer (2.2.5)
5. SVN (1.13.0)
6. Git (2.25.1)
7. Wget (1.20.3)

Before starting unit test in WordPress with PHPUnit, it is better to familiarize all this tools and confirm that it is working in our system.

## Plugin code

Here is the sample plugin code that copied from [Smashing Magazine](https://www.smashingmagazine.com/2017/12/automated-testing-wordpress-plugins-phpunit/){:target='_blank'}.

    <?php 

    class WP_Meta_Verify 
    {
        public function __construct()
        {
            add_action('wp_head', array($this, 'header_code'));
        }

        public function header_code()
        {
            $google_code = get_option('wpmv_google_code');
            $bing_code = get_option('wpmv_google_code');

            echo $this->google_site_verification($google_code);
            echo $this->bing_site_verification($bing_code);
        }

        public function google_site_verification($code)
        {
            return "<meta name=\"google-site-verification\" content=\"$code\">";
        }

        public function bing_site_verification($code)
        {
            return "<meta name=\"msvalidate.01\" content=\"$code\">";
        } 
    } 

    new WP_Meta_Verify();

This is a simple plugin that displays Google and Bing webmaster verification meta tags in the header of WordPress’ front end. In the plugin code, removed settings page related code to make our code simple.

### Step 1

Go to the tested plugin directory in our WordPress installation.

    cd /var/www/html/your-wordpress/wp-content/plugins/sample-plugin/

### Step 2

Now we need to include PHPUnit as development dependancy.

Create `composer.json` for the project if it is not exist.

    composer init

**Add PHPUnit**

    composer require --dev phpunit/phpunit

### Step 3

Generate the plugin test files.

    wp scaffold plugin-tests plugin-directory-name

##### Example

    wp scaffold plugin-tests sample-plugin

This command will generate all the files needed for running tests.

### Step 4

Initialize the testing environment locally.

    bash bin/install-wp-tests.sh test_database_name mysql_user_name 'mysql_user_password' database_host_name wp_version

##### Example

    bash bin/install-wp-tests.sh wp_test root 'znode123' localhost latest

### Step 5

Run the default test in `tests/test-sample.php` using PHPUnit command. Now we have included PHPUnit as library in our project. So we have to use relative path to run the test.

    ./vendor/bin/phpunit


#### Issue 1

When I run plugin test, first I got the below error message in the terminal.

>Error: The PHPUnit Polyfills library is a requirement for running the WP test suite.
>
>If you are trying to run plugin/theme integration tests, make sure the PHPUnit Polyfills library (https://github.com/Yoast/PHPUnit-Polyfills) is available and either load the autoload file of this library in your own test bootstrap before calling the WP Core test bootstrap file; or set the absolute path to the PHPUnit Polyfills library in a "WP_TESTS_PHPUNIT_POLYFILLS_PATH" constant to allow the WP Core bootstrap to load the Polyfills.
>
>If you are trying to run the WP Core tests, make sure to set the "WP_RUN_CORE_TESTS" constant to 1 and run `composer update -W` before running the tests.
>Once the dependencies are installed, you can run the tests using the Composer-installed version of PHPUnit or using a PHPUnit phar file, but the dependencies do need to be installed whichever way the tests are run."

**Fix**

PHPUnit Polyfills library is now required by WordPress tests to fix the version compatibility issues we often face with WordPress. So now we need to add a PHPUnit Polyfills library in the plugin as a development dependancy using Composer.

    composer require --dev yoast/phpunit-polyfills

Once the PHPUnit Polyfills library is available, include it in the first line of `sample-plugin/tests/bootstrap.php`.

    require dirname( dirname( __FILE__ ) ) . '/vendor/yoast/phpunit-polyfills/phpunitpolyfills-autoload.php';

### Step 6

Now it is the time to create actual test for our plugin. It is better to delete `tests/test-sample.php` file.

Create a `test-wp-meta-verify.php` file in the tests folder.

    <?php 

    class WP_Meta_VerifyTest extends WP_UnitTestCase
    {
        public function set_up()
        {
            parent::set_up();
            $this->class_instance = new WP_Meta_Verify();
        }

        public function test_google_site_verification()
        {
            $meta_tag = $this->class_instance->google_site_verification('B6wFaCRbzWE42SyxSvKUOyyPxZfJCb5g');
            $expected = '<meta name="google-site-verification" content="B6wFaCRbzWE42SyxSvKUOyyPxZfJCb5g">';

            $this->assertEquals($expected, $meta_tag);
        }

        public function test_bing_site_verification()
        {
            $meta_tag = $this->class_instance->bing_site_verification('B6wFaCRbzWE42SyxSvKUOyyPxZfJCb5g');
            $expected = '<meta name="msvalidate.01" content="B6wFaCRbzWE42SyxSvKUOyyPxZfJCb5g">';

            $this->assertEquals($expected, $meta_tag);
        }s
    }

Now again run the tests & we can see the result.

We can refer the guidelines from PHPUnit to make good test cases & structure.

1. [Writing Tests for PHPUnit](https://phpunit.readthedocs.io/en/9.5/writing-tests-for-phpunit.html){:target='_blank'}
2. [Organizing Tests](https://phpunit.readthedocs.io/en/9.5/organizing-tests.html){:target='_blank'}

There is too many blog post and tutorials about unit testing & how to write best tast cases. A google search is enough to find good articles.
