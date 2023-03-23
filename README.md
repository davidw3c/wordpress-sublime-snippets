# Wordpress & Advanced Custom Fields code snippets for Sublime Text
A collection of shortcodes to be used in the Sublime Text editor, which quickly and easily generate useful code snippets when developing websites using Wordpress and Advanced Custom Fields.

## The Shortcodes

### cptloop 

Stands for: "Custom Post Type Loop"

What it does: Generates a 'while loop' to loop through a Wodpress Custom Post type

The code that gets generated:

```php

<?php
$loop = new WP_Query(
    array(
        'post_type' => 'your_custom_post_type',
        'posts_per_page' => -1,
    )
);
while ( $loop->have_posts() ) : $loop->the_post();
?>
 
<h3><?php the_title(); ?></h3>
 
<?php endwhile;
wp_reset_postdata();
?>

```
