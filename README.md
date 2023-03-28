# Wordpress & Advanced Custom Fields code snippets for Sublime Text
A collection of shortcodes to be used in the Sublime Text editor, which quickly and easily generate useful code snippets when developing websites using Wordpress and Advanced Custom Fields.

## How to Install

### MacOS

On MacOS - Go to the folder where your Sublime Text Snippets are stored:

```
Users > yourname > Library > Application Support > Sublime Text 3 > Packages > User
```

And then copy the files from this Github repo ending in `.sublime-snippet` into this folder.

Note that you will need to show hidden files as Library will be hidden. (Command + Shift + . )

### Manually

You could also add the files manually, one by one, by opening Sublime Text > Tools > Developer > New Snippet

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
 
<h3><a href="<?php the_permalink(); ?>"><?php the_title(); ?></a></h3>
 
<?php endwhile;
wp_reset_postdata();
?>

```
