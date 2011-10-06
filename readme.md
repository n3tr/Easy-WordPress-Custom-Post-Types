## Usage

First, download the class, and drag it into the root of your theme directory. 

Next, within `functions.php`, require the class.

    require 'jw_custom_posts.php';

You now have access to the class and its functions. Instantiate the class.
We'll use a Snippet post type as an example.

    $snippet = new JW_Post_Type('Snippet');

You may also pass an optional second parameter to override some of the
defaults. For example, if I only want to provide support for a title and an
excerpt, I could do:

    $snippet = new JW_Post_Type('Snippet', array(
       'supports' => array('title, 'excerpt')
    );

### Custom Taxonies

It makes sense to filter our sample Snippet post type by difficulty and language. We can implement that functionality quite easily.

    $snippet->add_taxonomy('Difficulty');
    $snippet->add_taxonomy('Language');

I may also specify the plural form of my taxonomy, and any optional overrides. 

    $snippet->add_taxonomy('Difficulty', 'Difficulties', array(
      'show_ui' => false
    );

### Meta Boxes

Our Snippet post type should allow me to enter additional information about the
single snippet - perhaps a GitHub link, additional notes, an associated url for
the snippet, etc. 

    $snippet->add_meta_box('Snippet Info', array(
      'Associated URL' => 'text',
      'GitHub Link' => 'text',
      'Additional Notes' => 'textarea'
    ));

Within the second array argument, set the label text and the type of input to
display,respectively.