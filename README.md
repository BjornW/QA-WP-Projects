Using PHP Codesniffer for QA reviews of WordPress projects
=====================================================
[![Build Status](https://travis-ci.org/jrfnl/QA-WP-Projects.png?branch=master)](https://travis-ci.org/jrfnl/QA-WP-Projects)

## Introduction

Example code for a talk about how to use a variety of PHPCS rules and standards to get an indication of code quality for WP plugins and themes.

Also, have a look at the [slides from the talk](https://speakerdeck.com/jrf/leveraging-the-wordpress-coding-standards-to-review-plugins-and-themes).

**_Note: This repository will not be actively maintained. It is intended as example code only._**


## Installation

### Requirements

* PHP 5.4+.
* [Composer](https://getcomposer.org/download/)


### Installation

* Download the latest release of this repository or clone the repo via git.
* Go to the directory where you unzipped the release or cloned the repository to and run `composer install`.
    This will install the following dependencies:
    - PHP_CodeSniffer
    - WordPress Coding Standards
    - PHPCompatibility
    - PHPLOC
    - phpcodesniffer-composer-installer

Alternatively if you already have all the dependencies installed on your system, you can just register the standards contained in this repository with PHP_CodeSniffer.
* Run `phpcs config-show` to see the currently installed paths.
* Run `phpcs config-set installed_paths /path/to/already/installed/standards,/path/to/the/root/of/this/install


You can verify that the standards are registered correctly by running `./vendor/bin/phpcs -i` on the command line.
You should see at the very least the following standards:
- PHPCompatibility
- WordPress
- WP-QA-Basic
- WP-QA-Strict
(and a number of other ones, but if you see the above ones, you're good.


## Reviewing WordPress plugins and themes


### Before running the tool

To use this tool to review WordPress plugins and themes, the tool needs a little bit of information about the plugin/theme you want to review.

* Download the plugin/theme and unzip it. Make a note of the **path to the plugin/theme root directory**.
* Check with your webhost on which **version of PHP** your site is running.
* Open the `readme.txt` in the root of the plugin/theme directory and check what the **minimum supported WP version** is for the plugin/theme.
* Open the plugin main file or the theme `functions.php` file and check if it has a `Text Domain: my-plugin` header. If it has, make a note of the text domain. Otherwise, use the plugin/theme slug.
* "Guess" the prefixes the plugin/theme will use. Often this is the plugin/theme slug or an acronym based on the plugin/theme slug. For instance for `WordPress SEO by Yoast`, the prefixes might be (and are): `wpseo` and `yoast`


## How to run ?

Run the tool by opening the command line in the `vendor/bin` directory of this repository
vendor/bin> phpcs ./path/to/plugin-root/ --standard=WP-QA-Basic --report-full --report-source --report-summary --basepath=./path/to/plugin-root/ --runtime-set testVersion 5.6- --runtime-set minimum_supported_wp_version 4.5 --runtime-set prefixes plugin_prefix,plugin_acronym --ignore=./path/to/plugin-root/tests/ --runtime-set text_domain plugin-slug



## What does this check for ?




## How to interpret the results ?





## License

This code is released under the [MIT License](LICENSE).
