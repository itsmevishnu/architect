---
layout: post
title: Adding script to Wordpress themes
categories: wordpress
---

Welcome to my wordpress tutorials.Today let's learn how to include external css and javascript files to wordpress theme or plugin.

For this purpose there are some functions and hooks available in wordpress. Thanks for that. It reduces a lot of codes!. `admin_enqueue_scripts` is the hook used to add some extra css or js in our themes, or also in our plugins.
Also, `wp_enqueue_script` and `wp_enqueue_style` are two functions used to add scripts and stylesheets into wordpress respectively.

Let's see how these are used to add scripts.

{% highlight php %}
<?php 
function theme_admin_scripts() {

  //Adding js script.

	wp_enqueue_script( 'meta_box_script', get_template_directory_uri() . '/inc/js/theme_options_upload.js', array(), '1.0.0', true );

  //Adding stylesheet.

	wp_enqueue_style( 'theme_options', get_template_directory_uri() . '/inc/css/themeoptions.css' );
}
add_action( 'admin_enqueue_scripts', 'theme_admin_scripts' );

{% endhighlight %}

The above example used to add `theme_options_upload.js` and `theme_options.css` to the wordpress. This code snippet can add to either in `functions.php` or in a new plugin file. No issue. Boths are right.

Now lets check each functions seperately. `wp_enqueue_script` has 5 parameters. They are

* **String handle** - It's a simple name to identify and refer the script in file. And it *should be unique*.

* **String src** - It's the path of the file. I follow a general folder structure to keep my theme clean, like `/inc/js/` inside the theme folder.

* **Array dependency** - It's an optional parameter, an array of dependencies of the current script.

* **String / Bool / Null version** - It denotes the version of the file that used for cache busting. If its `'1'`, then the version of file is 1.0. If it set to false, then the version of wordpress taken as file version and if set to null, the file has no version.

* **Bool in_footer** - It's used to specify where the script will load. If it is `true`, then `<script>` tag will seen inside the `<body>` else in the `<head>`.

Hope you understand the first function. Then lets us move on to next function, `wp_enqueue_style`. This has also same parameters except last one, the last parameter is replaced `in_footer`.

* **String media** - Here we specify the media  for which this stylesheet is defined, like `print`,`screen`, or media queries like `(max-width:360px)` or `(orientation: portrait)` etc, default value is `all`.

Hope you understand the concepts and usage of these functions.

Thank you..
