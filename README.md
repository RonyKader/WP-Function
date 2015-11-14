# WP-Function
Root url for website
---------------------------------------------------------
<?php site_url(); ?> 
<?php bloginfo('url'); ?> 	

title of specific post/page 
---------------------------------------------------------
<?php wp_title(); ?> 

Title of site 
---------------------------------------------------------
<?php bloginfo('name'); ?> 

Site description 
---------------------------------------------------------
<?php bloginfo('description'); ?> 

stylesheet folder location 
---------------------------------------------------------
<?php get_stylesheet_directory(); ?> 		

style.css file location 
---------------------------------------------------------
<?php bloginfo('stylesheet_url'); ?> 	

pingback url 	
---------------------------------------------------------
<?php bloginfo('pingback_url'); ?> 	

Template folder path 
---------------------------------------------------------
<?php bloginfo('template_url'); ?> 		

wordpress site version 
---------------------------------------------------------
<?php bloginfo('version'); ?>

atom url 
---------------------------------------------------------
<?php bloginfo('atom_url'); ?> 	

rss2 url 
---------------------------------------------------------
<?php bloginfo('rss2_url'); ?> 
	
Html version 
---------------------------------------------------------
<?php bloginfo('html_type'); ?> 	

charset parameter
---------------------------------------------------------
<?php bloginfo('charset'); ?> 

==========================================================
Codes for Other Template Files
Codes below will be seen across all template files such as 
single.php, index.php, page.php and so on. Its really easy 
to call on these codes to make your theme dynamic when coding it.
==========================================================

Displays Header.php file content
---------------------------------------------------------
<?php get_header(); ?> 

Displays Footer.php file content
---------------------------------------------------------
<?php get_footer(); ?> 

Displays Sidebar.php file content
---------------------------------------------------------
<?php get_sidebar(); ?>

 Displays Comment.php file content
---------------------------------------------------------
<?php comments_template(); ?>

Displays the Content of the Post
---------------------------------------------------------
<?php the_content(); ?>

Displays the excerpt that is used in Posts
---------------------------------------------------------
<?php the_excerpt(); ?> 

Title of the Specific Post
---------------------------------------------------------
<?php the_title(); ?>
    
Link of the Specific Post
---------------------------------------------------------
<?php the_permalink() ?>

Category of a Specific Post
---------------------------------------------------------
<?php the_category(', ') ?>

Author of the Specific Post
---------------------------------------------------------
<?php the_author(); ?>

ID of a Specific Post
---------------------------------------------------------
<?php the_ID(); ?> – 

Edit link for a Post
---------------------------------------------------------
<?php edit_post_link(); ?>

URL of the Next Page
---------------------------------------------------------
<?php next_post_link(' %link ') ?>

URL of the Previous Page
---------------------------------------------------------
<?php previous_post_link('%link') ?>

Lists all links in Blogroll
---------------------------------------------------------
<?php get_links_list(); ?>

Lists all Pages
---------------------------------------------------------
<?php wp_list_pages(); ?>

List Archive for the Site
---------------------------------------------------------
<?php wp_get_archives() ?>

Lists all Categories
---------------------------------------------------------
<?php wp_list_cats(); ?>

Displays the Built in Calendar
---------------------------------------------------------
<?php get_calendar(); ?>

Displays Register Link
---------------------------------------------------------
<?php wp_register(); ?>

Displays Login/Logout Link only to Registered Users
---------------------------------------------------------
<?php wp_loginout(); ?>

the date is ’02-15-14′
---------------------------------------------------------
<?php the_time('m-d-y'); ?>

link to comments of post
---------------------------------------------------------
<?php comments_popup_link(); ?>

edit link of post/page
---------------------------------------------------------
<?php edit_post_link(); ?>

links from blogroll
---------------------------------------------------------
<?php wp_list_bookmarks(); ?>

list all pages
---------------------------------------------------------
<?php wp_list_pages(); ?>

list all categories
---------------------------------------------------------
<?php wp_list_categories(); ?>

url to next post
---------------------------------------------------------
<?php next_post_link('%link'); ?>

url to previous post
---------------------------------------------------------
<?php previous_post_list('%link'); ?>

next and previous post link
---------------------------------------------------------
<?php posts_nav_link(); ?>

rewinds post for a second loop
---------------------------------------------------------
<?php rewind_posts(); ?>

admin meta data
---------------------------------------------------------
<?php wp_meta(); ?>


==========================================================
The Loop (Basic Loop)
==========================================================
<?php if(have_posts()) { ?> 	
<?php while(have_posts()) { ?> 	
<?php the_post(); ?> 	
<?php // custom post content code for title, excerpt and featured image ?> 	
<?php } // end while ?> 	
<?php } // end if ?>

==========================================================
The Loop (Advance Loop)
==========================================================
<?php if (have_posts()) : ?>
    <?php while (have_posts()) : the_post(); ?>
    <div class="post" id="post-<?php the_ID(); ?>">
        <h2><a href="<?php the_permalink() ?>" rel="bookmark" title="Permanent Link to
        <?php the_title(); ?>"><?php the_title(); ?></a></h2>
        <small><?php the_time('F jS, Y') ?> <!-- by <?php the_author() ?> --></small>
         
        <div class="entry">
            <?php the_content('Read the rest of this entry »'); ?>
        </div>
         
        <p class="postmetadata">Posted in <?php the_category(', ') ?> <strong>|</strong>
            <?php edit_post_link('Edit','','<strong>|</strong>'); ?>
            <?php comments_popup_link('No Comments »', '1 Comment »', '% Comments
        »'); ?>
        </p>
    </div>
    <?php endwhile; ?>
    <div class="navigation">
        <div class="alignleft"><?php next_posts_link('« Previous Entries') ?></div>
        <div class="alignright"><?php previous_posts_link('Next Entries »') ?></div>
    </div>
<?php else : ?>
    <h2 class="center">Not Found</h2>
    <p class="center">Sorry, but you are looking for something that isn't here.</p>
    <?php include (TEMPLATEPATH . "/searchform.php"); ?>
<?php endif; ?>

==========================================================
Navigation Menu
Navigation Menu (Default)
==========================================================
<?php wp_nav_menu(); ?>

Navigation Menu (Specific)
---------------------------------------------------------
<?php wp_nav_menu( array('menu' => 'Project Nav' )); ?>

Navigation Menu (Category Based)
---------------------------------------------------------
<ul id="menu"> 	
<li <?php if(is_home()) { ?> class="current-cat" <?php } ?>> 	
<a href="<?php bloginfo('home'); ?>">Home</a></li> 	
<?php wp_list_categories('title_li=&orderby=id');?> 	
</ul>

Navigation Menu (Page Based)
---------------------------------------------------------
<ul id="menu"> 	
<li <?php if(is_home()) { ?> class="current-page-item" <?php } ?>> 	
<a href="<?php bloginfo('home'); ?>">Home</a></li> 	
<?php wp_list_pages('sort_column=menu_order&depth=1&title_li=');?> 	
</ul>

Comments popup link
---------------------------------------------------------
<?php comments_popup_link( 'Leave a Comment', '1 Comment', '% Comments' ); ?>


if statemant for post find/search
---------------------------------------------------------
<?php if(have_posts()) : ?>

while statemant
---------------------------------------------------------
<?php while(have_posts()) : the_post(); ?>

End while statemant
---------------------------------------------------------
<?php endwhile; ?>

End if statemant
---------------------------------------------------------
<?php endif; ?>

==========================================================
Get Featured Image URL with Proper size Array
==========================================================
<?php $src = wp_get_attachment_image_src( get_post_thumbnail_id($post->ID), array( 900,900 ), false, '' ); echo $src[0]; ?>


Feature iamge query with direct hyperlink
---------------------------------------------------------
<?php
$thumbnail_id=get_the_post_thumbnail($post->ID);
preg_match ('/src="(.*)" class/',$thumbnail_id,$link);
echo $link[1];
?>

Feature iamge query with direct link for Lightbox
---------------------------------------------------------
<?php
$thumbnail_id=get_the_post_thumbnail($post->ID);
preg_match ('/src="(.*)" class/',$thumbnail_id,$link);
echo $link[1];
?>
<a href="<?php echo $link[1]; ?>" rel="lightbox"><?php the_post_thumbnail('thumbnail'); ?></a>

==========================================================
Display all Custom Texonomies list
==========================================================
<?php
//list terms in a given taxonomy
$taxonomy = 'recipe-cat';
$tax_terms = get_terms($taxonomy);
?>
<ul class="fc_texonomy">
<?php
foreach ($tax_terms as $tax_term) {
echo '<li>' . '<a href="' . esc_attr(get_term_link($tax_term, $taxonomy)) . '" title="' . sprintf( __( "View all posts in %s" ), $tax_term->name ) . '" ' . '>' . $tax_term->name.'</a></li>';
}
?>
</ul>

==========================================================
URL / permalink rewrite issue fix for (Recipe) Custom Post
==========================================================
add_action('init', 'firmasite_resimlitarif_cpt', 0);
function firmasite_resimlitarif_cpt() 
{
// Recipe Custom Post
  $args = array(
    'public' => true,
    'show_in_menu' => true, 
    'permalink_epmask' => EP_NONE,
    'rewrite' => array('slug'=>'/','with_front'=>false),
    'has_archive' => false,
    'supports' => array('title','editor','thumbnail')
  ); 
  register_post_type('recipe',$args);
}
add_action("parse_query", 'firmasite_resimlitarif_parse_query');
function firmasite_resimlitarif_parse_query($query) {
    global $wp, $wp_rewrite;
    // Is this query for /%post_name%/? Is it main request query?
    if (isset($query->query['name'])
        && substr($wp->matched_rule, 0, 7) == "([^/]+)"
        && isset($query->query)
        && isset($wp->query_vars)
        && $query->query == $wp->query_vars)
    {
        if (!($post_types = get_query_var("post_type"))) {
            if ($wp_rewrite->permalink_structure == "/%postname%/")
                $post_types = array("post");
            else
                $post_types = array();
        }
        if (is_array($post_types)){ 
            $post_types[] = 'recipe';
            $post_types[] = 'page';
        }
        set_query_var("post_type", $post_types);
    } 
}
==========================================================
Add metabox, save data in post, page, post-type
==========================================================
// Little function to return a custom field value
function wpshed_get_custom_field( $value ) {
	global $post;
    $custom_field = get_post_meta( $post->ID, $value, true );
    if ( !empty( $custom_field ) )
	    return is_array( $custom_field ) ? stripslashes_deep( 
$custom_field ) : stripslashes( wp_kses_decode_entities( $custom_field ) );
    return false;
}
// Add the Metabox
function wpshed_add_custom_meta_box() {
	add_meta_box( 'wpshed-meta-box', __( 'Metabox Example', 'textdomain' ), 'wpshed_meta_box_output', 'post', 'normal', 'high' );
	add_meta_box( 'wpshed-meta-box', __( 'Metabox Example', 'textdomain' ), 'wpshed_meta_box_output', 'page', 'normal', 'high' );	
	add_meta_box( 'wpshed-meta-box', __( 'Metabox Example', 'textdomain' ), 'wpshed_meta_box_output', 'post_type_name', 'normal', 'high' ); //show in custom post
}
add_action( 'add_meta_boxes', 'wpshed_add_custom_meta_box' );
// Output the Metabox
function wpshed_meta_box_output( $post ) {
	// create a nonce field
	wp_nonce_field( 'my_wpshed_meta_box_nonce', 'wpshed_meta_box_nonce' ); ?>	
	<p>
		<label for="wpshed_textfield"><?php _e( 'Textfield', 'textdomain' ); ?>:</label>
		<input type="text" name="wpshed_textfield" id="wpshed_textfield" value="<?php echo wpshed_get_custom_field( 'wpshed_textfield' ); ?>" size="50" />
    </p>
	<p>
		<label for="wpshed_textarea"><?php _e( 'Textarea', 'textdomain' ); ?>:</label><br />
		<textarea name="wpshed_textarea" id="wpshed_textarea" cols="60" rows="4"><?php echo wpshed_get_custom_field( 'wpshed_textarea' ); ?></textarea>
    </p>
	<?php
}
// Save the Metabox values
function wpshed_meta_box_save( $post_id ) {
	// Stop the script when doing autosave
	if( defined( 'DOING_AUTOSAVE' ) && DOING_AUTOSAVE ) return;
	// Verify the nonce. If insn't there, stop the script
	if( !isset( $_POST['wpshed_meta_box_nonce'] ) || !wp_verify_nonce( $_POST['wpshed_meta_box_nonce'], 'my_wpshed_meta_box_nonce' ) ) return;
	// Stop the script if the user does not have edit permissions
	if( !current_user_can( 'edit_post' ) ) return;
    // Save the textfield
	if( isset( $_POST['wpshed_textfield'] ) )
		update_post_meta( $post_id, 'wpshed_textfield', esc_attr( $_POST['wpshed_textfield'] ) );
    // Save the textarea
	if( isset( $_POST['wpshed_textarea'] ) )
		update_post_meta( $post_id, 'wpshed_textarea', esc_attr( $_POST['wpshed_textarea'] ) );
}
add_action( 'save_post', 'wpshed_meta_box_save' );
==========================================================
Conditional Metabox data returns (Example)
==========================================================
<?php global $post; 
$a=get_post_meta($post->ID,'pricing_class',true); 
if ($a){ 
echo $a; 
} 
?>

==========================================================
Query Recent 10 Post title From a Category
==========================================================
<?php
//display 10 posts for category id 47
    $args=array(
      'cat' => 1,
      'post_type' => 'post',
      'post_status' => 'publish',
      'posts_per_page' => 10,
      'caller_get_posts'=> 1
      );
    $my_query = null;
    $my_query = new WP_Query($args);
    if( $my_query->have_posts() ) {
      echo 'List of Posts';
      while ($my_query->have_posts()) : $my_query->the_post(); ?>
      <p><a href="<?php the_permalink() ?>" rel="bookmark" title="Permanent Link to <?php the_title_attribute(); ?>"><?php the_title(); ?></a></p>
       <?php
      endwhile;
    }
wp_reset_query();  // Restore global post data stomped by the_post().
?>

==========================================================
Add Menu Support in Theme
==========================================================
function register_my_menus() {
	register_nav_menus( array(
		'primary' => __( 'Primary Navigation', 'portfolium' ),
	) );
}

Show Menu In wordpress Header
----------------------------------------------------------
<?php wp_nav_menu( array( 'container_class' => 'menu-header', 'theme_location' => 'primary' ) ); ?>	

ADD icon in menu Li
----------------------------------------------------------
<?php
if (function_exists('wp_nav_menu')) {
wp_nav_menu(
array( 'theme_location'=> 'wpj-main-menu',
'menu_class' => 'nav navbar-nav',
'link_before' => '<i class="glyphicon-plus">&nbsp;</i>',
'link_after' => '<i class="glyphicon-plus">&nbsp;</i>',
'fallback_cb' => 'wpj_default_menu'
));}
else {wpj_default_menu();}
?>


==========================================================
Register sidebars and widget areas
==========================================================
function fctheme_widget_areas() {		
	 register_sidebar( array(
		'name' => __( 'About Us Page Content', 'freelancingcare' ),
		'id' => 'about_us_text',
		'before_widget' => '<div class="contact_map floatleft">',
	        'after_widget' => '</div>',
	        'before_title' => '<h3>',
	        'after_title' => '</h3>',
	    ) );		
}
add_action('widgets_init', 'fctheme_widget_areas');

Use Widget Code in Template Page
----------------------------------------------------------
	<?php if ( !function_exists('dynamic_sidebar') || !dynamic_sidebar(about_us_text) ) : ?>
			<div class="fc_class">			
			//Write your default data	
			</div>	
		<?php endif; ?>

==========================================================
Get author list in particular post category sort by post count
==========================================================
<?php
$catauthors = array();
$my_cat_id=5; // Your category ID
$allposts=get_posts("cat=$my_cat_id&showposts=-1");
if ($allposts) {
  foreach($allposts as $authorpost) {
    $catauthors[$authorpost->post_author]+=1; // Authors Post Limit 
  }
  arsort($catauthors); //sort array in reverse order by number of posts
  foreach($catauthors as $key => $author_post_count) {
    $curuser = get_userdata($key);
    $author_post_url=get_author_posts_url($curuser->ID, $curuser->nicename);
    echo '<p>--User nicename: '.$curuser->user_nicename .', display name: '. $curuser->display_name . ', number of posts in category '.$my_cat_id.': ' .$author_post_count .', link to all posts by this author:  <a href="' . $author_post_url . '" title="' . sprintf( __( "Posts by %s" ), $curuser->user_nicename ) . '" ' . '>' . $curuser->user_nicename .'</a></p>';
  }
}
?>

Another Easy code for author list 
----------------------------------------------------------
<?php wp_list_authors('show_fullname=1&optioncount=1&orderby=post_count&order=DESC&number=3'); ?>


==========================================================
Count all the post for a category
==========================================================
<?php
$counter = "SELECT COUNT(*) 
FROM $wpdb->posts
LEFT JOIN $wpdb->term_relationships ON($wpdb->posts.ID = $wpdb->term_relationships.object_id)
LEFT JOIN $wpdb->term_taxonomy ON($wpdb->term_relationships.term_taxonomy_id = $wpdb->term_taxonomy.term_taxonomy_id)
WHERE $wpdb->term_taxonomy.term_id = 5 
AND $wpdb->term_taxonomy.taxonomy = 'category'
AND $wpdb->posts.post_status = 'publish'
AND post_author = '1'
";
$user_count = $wpdb->get_var($counter);
echo $user_count;
?>


==========================================================
Conditional Text for Logged user and guest in wordpres
==========================================================
<?php if ( !is_user_logged_in() ) {
   echo 'Guest Data';
} else {
    echo 'Member data';
}
?>


==========================================================
Activate ReduxFramework Admin Panel
==========================================================
// Include the Redux theme options Framework
if ( !class_exists( 'ReduxFramework' ) ) {
	require_once( dirname( __FILE__ ) . '/ReduxCore/framework.php' );
}
// Tweak the Redux framework, Register all the theme options, Registers the wpex_option function
if ( !isset( $redux_demo ) ) {
	require_once( dirname( __FILE__ ) . '/functions/admin-config.php' );
}
