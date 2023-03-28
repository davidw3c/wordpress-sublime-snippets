# Wordpress & Advanced Custom Fields code snippets for Sublime Text
A collection of shortcodes to be used in the Sublime Text editor, which quickly and easily generate useful code snippets when developing websites using Wordpress and Advanced Custom Fields.

## How to Install

### Linux 

1. Open Terminal
2. CD to `/home/yourusername/.config/sublime-text/Packages/User` - obviously 'yourusername' being replaced with your actual user!
3. Type `xdg-open .` to open this folder
4. Copy the files from this repo ending in `.sublime-snippet` into this folder
5. Restart Sublime

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
$loop = new WP_Query( array( 
	'post_type' => 'yourposttypehere',
	'posts_per_page' => -1 
)); 
?>

<?php if ($loop->have_posts()): ?>
	<?php while ( $loop->have_posts() ) : $loop->the_post(); ?>

		<?php if (get_the_post_thumbnail()): ?>
			<?php the_post_thumbnail( 'custom_size_here' ); ?>
		<?php else: ?>
			Show fallback image
		<?php endif ?>

		<h3><a href="<?php the_permalink(); ?>"><?php the_title(); ?></a></h3>
		<p><?php the_time(get_option( 'date_format' )); ?></p>
		<p><?php echo get_the_excerpt(); ?></p>

	<?php endwhile; wp_reset_query(); ?>
<?php endif; ?>

```

### acfflexible

```
<?php if( have_rows('flexiblecontentfieldname') ): ?>
	<?php while ( have_rows('flexiblecontentfieldname') ) : the_row(); ?>

		<?php if( get_row_layout() == 'paragraph' ): ?>

			<?php echo get_sub_field('text'); ?>

		<?php elseif( get_row_layout() == 'download' ): ?>

			<?php echo get_sub_field('file'); ?>

		<?php endif; ?>

	<?php endwhile; ?>
<?php endif; ?>
```

### acfgallery

```
<?php 
$field_name_here = get_field('field_name_here');
if( $field_name_here ): ?>
    <div>
        <?php foreach( $field_name_here as $image ): ?>
        	<div>
                <a href="<?php echo esc_url($image['url']); ?>">
                     <img src="<?php echo esc_url($image['sizes']['thumbnail']); ?>" alt="<?php echo esc_attr($image['alt']); ?>" />
                </a>
            </div>    
        <?php endforeach; ?>
    </div>
<?php endif; ?>
```

### acfrelationship

```
<?php
$relationship_fieldname = get_field('relationship_fieldname');
if( $relationship_fieldname ): ?>
    <ul>
    <?php foreach( $relationship_fieldname as $post ): 

        // Setup this post for WP functions (variable must be named ).
        setup_postdata($post); ?>
        <li>
            <a href="<?php the_permalink(); ?>"><?php the_title(); ?></a>
        </li>
    <?php endforeach; ?>
    </ul>
    <?php 
    // Reset the global post object so that the rest of the page works correctly.
    wp_reset_postdata(); ?>
<?php endif; ?>
```
### acfrepeater

```
<?php if( have_rows('repeater_field_name') ): ?>
	<?php while ( have_rows('repeater_field_name') ) : the_row(); ?>

		<?php echo get_sub_field('sub_field_name'); ?>

	<?php endwhile; ?>
<?php endif; ?>
```
