---
title: "WordPress Plugin Development: Developer Notes 2024"
excerpt: In this article, I am sharing all the required WordPress Plugin Development notes with all the PHP / WordPress Developers. We will see hooks, filters, PHP functions and many more..
date: July 15, 2024
layout: post
author: neha
categories:
    - wordpress
image: assets/techalgospotlight-wordpress-banner.webp
keywords: wordpress plugin development
published: true
tags: featured
---

In this article, I am sharing all the required WordPress Plugin Development notes with all the PHP / WordPress Developers. We will see hooks, filters, PHP functions and many more.

What is WordPress?
------------------

WordPress (WP) is a content management system that uses PHP to dynamically generate pages from its MySQL database.

Since it started as a blogging platform, WordPress sites are organized into pages (eg. activity, about page, etc.) and posts (blog posts.) WP provides an easy backend console to deal with this and create pages and posts, but its true value comes in its extendibility with plugins and customization with code.


* * *

### Introduction

The main bulk of plugin development will deal with introducing new **actions** and **functions** hooked onto the WP core, as well as coding in custom PHP and MySQL queries to interact with, and modifying the MySQL database that WP comes packed in with. **Plugins are written in PHP.** Wrap them in <?php and ?> tags!


* * *

For WP to recognize that a . PHP file is a plugin, you need to ensure that you include a comment detailing the description and other metadata for the plugin as a whole!

```php
/*
Plugin Name: <PLUGIN NAME HERE>
Plugin URI: <PLUGIN DESCRIPTION URL>
Description: <PLUGIN DESCRIPTION>
Version: <PLUGIN VERSION>
Text Domain: <FOR TRANSLATIONS>
Domain Path: <FILE DIRECTORY FOR TRANSLATIONS>
Author: methylDragon
Author URI: methylDragon.com
License: <LICENSE>
*/
```


Also, **FYI**, whenever you open a parenthesis, make sure you add a space after it, otherwise WP will reject the code…

**some_function( 'see_the_parentheses?' );**


* * *

### Actions, Filters, and Hooks in WordPress

To deal with constant WP updates while maintaining plugin compatibility, WP has implemented a system called Actions, Filters, and Hooks to do this. This will form the bulk of any plugin development.


* * *

### A Refresher on PHP Functions in WordPress

Here’s a PHP function prototype refresher!


```php
function functionName() {
    code to be executed;
} 
```


You can call functions directly on WP using **functionName()**; , or call them via an action, or filter! You’ll see why this is useful later on.


* * *

### Hooks in WordPress

Hooks are provided by WordPress to allow your plugin to ‘hook into’ the rest of WordPress; that is, to call functions in your plugin at specific times, and thereby set your plugin in motion. (From WP codex)


**These hooks exist in two forms, Actions, and Filters.**


* * *

### Actions: Call PHP functions that are supposed to do something

Actions are places where WP or other plugins call certain functions. You _can_ write your own actions, and call them either alone, or _as a callback_ alongside another action! The latter is the reason why an action can be a hook since an action that you write can be hooked onto another action!

*   The difference between calling a function directly and using an action is that when you call a function using an action, any other actions that are hooked onto that action you just called will also end up being called.


* * *

### do\_action() and do\_action\_ref\_array() in WordPress

```php
/* Use do_action() to call a function anywhere you want

do_action( string $tag,  $arg = '' )

OPTIONAL: $arg (mixed) You can pass arguments to the action!
*/

	do_action( 'function_name' );

/* Use do_action_ref_array() to call a function anywhere you want, while passing an array as an argument!
*/

	$args = array( 'arg_1', true, 'foo', 'arg_4' );
	do_action_ref_array( 'function_name', $args );

	//Is equivalent to

	do_action( 'function_name', 'arg_1', true, 'foo', 'arg_4' );
```


* * *

### add\_action() in WordPress

```php
/* Use add_action() to hook an action onto another existing action
It will call your hooked action whenever the first action is called

add_action( string $tag, callable $function_to_add, int $priority = 10, int $accepted_args = 1 )

OPTIONAL: $priority (int) Used to specify the order in which functions associated with a particular action are executed. Lower number means higher priority. Functions with the same priority number are executed in the order in which they were added to the action. Default = 10

OPTIONAL: $accepted_args (int) The number of arguments the function accepts. . Default = 1

NOTE: The arguments passed to the $tag action will be the ones passed to the $function_to_add
*/
	add_action( 'some_hook', 'callback_function_for_some_hook' );

// Or if calling a function from within a class
	add_action( 'some_hook', array( 'some_class', 'callback_function_in_some_class' ) );
```


* * *

### Unhooking actions in WordPress

```php
/* Use remove_action() to unhook an action
Note: You cannot call this directly, it has to be done from within a function!

This returns true when finished
*/
	function remove_my_action() {
		remove_action( 'some_hook', 'function_being_removed' );
	}
	do_action( 'remove_my_action' );

// Or if the action was hooked from within a class, eg. by a plugin
	function remove_my_class_action(){
		global $my_class;
		remove_action( 'some_hook', array( $my_class, 'class_function_being_removed' ) );
	do_action( 'remove_my_class_action');
	}

/* Use remove_all_actions() to unhook everything hooked to an action

This returns true when finished

Note: Becareful when using this, because it might cause issues with nested hooks!
*/
	remove_all_actions( 'some_hook' );
```


* * *

```php
/* Use has_action() to check if an action has been registered for a hook.
It returns a boolean value, or an integer, if the action has a priority value associated with it
*/
	has_action( 'hook_name', 'function_to_check' );

// Use did_action() to see how many times an action has fired
	did_action( 'action_name' )
```


* * *

### Filters: Call PHP functions that receive and return values

> Note: They might potentially modify the received value, but they must return a value

Otherwise, filters act a lot like actions, you can add, and do them just like actions, but with a few small differences. **Just make sure your functions are defined to be called by filters take in and RETURN values!**

I’ll add less detail for the filter functions because a lot of them are aliases for the action functions


* * *

### apply\_filters() in WordPress

```php
/* An analog is do_action()

apply_filters( string $tag, mixed $value )

You must supply a parameter!
*/
	apply_filters( 'filter_to_use', 'value_to_filter', 'potentially_more_values' );
```


* * *

### add\_filter() in WordPress

```php
/* So let's say you might want to add additional filters onto filter_to_use. You use add_filter to hook an additional filter function to an existing filter, much like add_action!

add_filter( string $tag, callable $function_to_add, int $priority = 10, int $accepted_args = 1 )

Same thing with priority and accepted args for add_action

Note: Don't forget to define your callback function!
*/
	function additional_filter( $example ) {
    	// Maybe modify $example in some way.
    	return $example;
	}

	add_filter( 'filter_to_use', 'additional_filter' );
```


* * *

### Unhooking filters in WordPress

```php
/* remove_filter(): Same thing with actions, self explanatory
Returns true when done
*/
	function remove_my_filter() {
		remove_filter( 'some_hook', 'function_being_removed' );
	}
	do_action( 'remove_my_filter' );

// Or if the filter was hooked from within a class, eg. by a plugin
	function remove_my_class_filter(){
		global $my_class;
		remove_filter( 'some_hook', array( $my_class, 'class_function_being_removed' ) );
	do_action( 'remove_my_class_filter' );
	}

// remove_all_filters() does exactly what you think it does
	remove_all_filters( 'some_hook' );
```


* * *

```php
// current_filter() retrieves the name of the current filter or action

	//Retrieving filter name
		function my_filter() {
	  	  echo current_filter(); // 'the_content'
		}
		add_filter( 'the_content', 'my_filter' );

	//Retrieving action name
		function my_init_function() {
	  	  echo current_filter(); // 'init'
		}
		add_action( 'init', 'my_init_function' );

// has_filter() works like has_action(), returns true if a hook has the passed function hooked onto it
	has_filter( 'hook_name', 'function_to_check' )
```


* * *

More Plugin Development Links
-----------------------------

[https://codex.wordpress.org/Plugin\_API](https://codex.wordpress.org/Plugin\_API)  
[https://www.youtube.com/watch?v=AQrXcsc4CIw](https://www.youtube.com/watch?v=AQrXcsc4CIw) (Actions, Filters, and Hooks)  
[https://www.youtube.com/watch?v=w257tYZtL8Y](https://www.youtube.com/watch?v=w257tYZtL8Y) (WordPress Plugin Development)  
[https://wordpress.stackexchange.com/questions/1007/difference-between-filter-and-action-hooks](https://wordpress.stackexchange.com/questions/1007/difference-between-filter-and-action-hooks) (Filters vs Actions)