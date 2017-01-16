---
layout: post
title: Custom role creation in wordpress.
categories: wordpress
---
Welcome to my wordpress tutorials and tips. Today let's learn how we can create a custom role in wordpress with out any plugins.

Wordpress, by out of box support 5 user roles such as `Adiministrator`, `Editor`,`Author`, `Contributer` and `subscriber`. But most of the case, we need some extra roles for performing some extra actions or hide some privillages. Whatever may be, less go throuh how can we do it with out any plugin.

{% highlight php %}
<?php

function samples_add_new_role(){
	$capabilities = array('delete_posts'     => true,
					'delete_published_posts' => true,
					'edit_posts'             => true,
					'edit_published_posts'   => true,
					'publish_posts'          => true,
					'read'                   => true,
					'upload_files'           => true
					);
	add_role( 'post_builder', 'Post Builder', $capabilities );
}
add_action( 'init', 'samples_add_new_role' );
?>
{% endhighlight %}

Now let's check the code now. `samples_add_new_role` is a call back function which is fired when the theme is loaded here, since I hooked the function to `init`. `add_role` is the function used to create a custom user role. Now let's look the parameter of this function in detail.

* **String role name** - The role name, it is used to access the role.

* **Sting disply name** - Shows the display name, that is what we have to seen in the back end user role option.

* **Array capabilities** - Here we specify a set of actions that can be perform by new user role.

Hope you will try it yourself.

Thank you.
