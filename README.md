iView
=====

iView is easy to use jQuery image slider with animated captions, responsive layout and HTML Elements like (Video, iFrame) slider. Easily add unlimited number of slides and captions. Use it as image slider, image gallery, banner rotator, banner ads, or even presentation.

A) Setup
=====

Include the following javascript and css code into HEAD section of the page:

<link rel="stylesheet" href="iview.css" type="text/css" media="screen" />
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js" type="text/javascript"></script>
<script src="raphael-min.js" type="text/javascript"></script>
<script src="jquery.easing.js" type="text/javascript"></script>
<script src="iview.packed.js" type="text/javascript"></script>

Then insert into body section the slide (or slides) to which you want to apply the effect.

<div id="iview">
    <!-- Slide 1 -->
    <div data-iview:thumbnail="photos/photo1_thumb.jpg" data-iview:image="photos/photo1.jpg"></div>
    <!-- Slide 2 -->
    <div data-iview:thumbnail="photos/photo2_thumb.jpg" data-iview:image="photos/photo2.jpg"></div>
</div>
You can add a caption to the slide, just put a div with class "iview-caption" into the div above:

<div id="iview">
    <!-- Slide 1 -->
    <div data-iview:thumbnail="photos/photo1_thumb.jpg" data-iview:image="photos/photo1.jpg">
        <!-- Caption -->
        <div class="iview-caption" data-x="0" data-y="0" data-width="400" data-height="300" data-transition="wipeRight" data-speed="700"><h3>The Responsive Caption</h3>This is the product that you <b><i>all have been waiting for</b></i>!<br><br>Customize this slider with just a little HTML and CSS to your very needs. Give each slider some captions to transport your message.<br><br>All in all it works on every browser (including IE6 / 7 / 8) and on iOS and Android devices!</div>
    </div>
    <!-- Slide 2 -->
    <div data-iview:thumbnail="photos/photo2_thumb.jpg" data-iview:image="photos/photo2.jpg">
        <!-- Caption -->
        <div class="iview-caption" data-x="70" data-y="70" data-transition="expandLeft">Caption Description</div>
    </div>
</div>
By adding one more html5 data-attribute to the "iview-caption" div you can decide the effect of the caption. The possible effects are: "wipeLeft", "wipeRight", "wipeTop", "wipeBottom", "expandLeft", "expandRight", "expandTop", "expandBottom", "fade"


<div class="iview-caption" data-transition="fade">Caption description</div>
A caption can have a data-transition "fade", in this case it will be displayed with a fading effect.
More HTML5 data-attributes avalable:

Parameter	Accepted values

data-transition	Transition type can be any one of the following: "wipeLeft", "wipeRight", "wipeTop", "wipeBottom", "expandLeft", "expandRight", "expandTop", "expandBottom", "fade"
data-easing	for the complete list http://jqueryui.com/demos/effect/easing.html
data-speed	Transition duration in milliseconds.
data-x	Caption x position in pixel.
data-y	Caption y position in pixel.
data-width	Caption width in pixel, if not set will get the source caption width.
data-height	Caption height in pixel, if not set will get the source caption height.

VIDEOS
=====

To include a video into your slideshow you must put an iframe into one of your slides:


<div data-iview:image="photos/photo.jpg">
    <!-- Video iFrame -->
    <iframe src="http://player.vimeo.com/video/11475955?byline=1&portrait=0" width="100%" height="100%" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
 
    <!-- Caption -->
    <div class="iview-caption" data-x="70" data-y="70" data-transition="expandLeft">Caption Description</div>
</div>
As you can see I set the width and the height of the iframe to 100%, so it changes its size according with the size of the slideshows (I mean the iframe, the video in the iframe will mantain its ratio).

Finally you need to hook up your script using the $(document).ready() function:

<script type="text/javascript">
$(document).ready(function() {
    $('#slider').iView();
});
</script>

B) Available Parameters
=====

The iView Slider has plenty of options to fiddle with. Below is an example of the code with all available options and their defaults:


<script type="text/javascript">
$(document).ready(function() {
    $('#slider').iView({
        fx: 'random', // Specify sets like: 'left-curtain,fade,zigzag-top,strip-left-fade'
        easing: 'easeOutQuad', // for the complete list http://jqueryui.com/demos/effect/easing.html
        strips: 20, // Number of strips for strip animations
        blockCols: 10, // Number of block columns for block animations
        blockRows: 5, // Number of block rows for block animations
        captionSpeed: 500, // Caption transition speed
        captionEasing: 'easeInOutSine', // Caption transition easing effect
        captionOpacity: 1, // Caption opacity
        animationSpeed: 500, // Slide transition speed
        pauseTime: 5000, // How long each slide will show
        startSlide: 0, // Set starting Slide (0 index)
        directionNav: true, // Next & Previous navigation
        directionNavHoverOpacity: 0.6, // Fade on hover
        controlNav: true, // 1,2,3,4... navigation
        controlNavNextPrev: true, // previous,next navigation
        controlNavHoverOpacity: 0.6, // Navigation fade on hover
        controlNavThumbs: false, // Show thumbs navigation
        controlNavTooltip: true, // Show tooltip image previewer
        autoAdvance: true, // Force auto transitions
        keyboardNav: true, // Use left & right arrows
        touchNav: true, // Use Touch swipe to change slides
        pauseOnHover: false, // Stop slider while hovering
        nextLabel: "Next", // To set the string of the next button (Multilanguage use)
        previousLabel: "Previous", // To set the string of the previous button (Multilanguage use)
        playLabel: "Play", // To set the string of the play button (Multilanguage use)
        pauseLabel: "Pause", // To set the string of the pause button (Multilanguage use)
        closeLabel: "Close", // To set the string of the close button (Multilanguage use)
        randomStart: false, // Start on a random slide
        timer: 'Pie', // Timer style: "Pie", "360Bar" or "Bar"
        timerBg: '#000', // Timer background
        timerColor: '#EEE', // Timer color
        timerOpacity: 0.5, // Timer opacity
        timerDiameter: 30, // Timer diameter
        timerPadding: 4, // Timer padding
        timerStroke: 3, // Timer stroke width
        timerBarStroke: 1, // Timer Bar stroke width
        timerBarStrokeColor: '#EEE', // Timer Bar stroke color
        timerBarStrokeStyle: 'solid', // Timer Bar stroke style
        timerX: 10, // Timer X position threshold
        timerY: 10, // Timer Y position threshold
        tooltipX: 5, // Tooltip X position threshold
        tooltipY: -5, // Tooltip Y position threshold
        onBeforeChange: function(){}, // Triggers before a slide transition
        onAfterChange: function(){}, // Triggers after a slide transition
        onSlideshowEnd: function(){}, // Triggers after all slides have been shown
        onLastSlide: function(){}, // Triggers when last slide is shown
        onAfterLoad: function(){}, // Triggers when slider has loaded
        onPause: function(){}, // Triggers when slider has paused
        onPlay: function(){} // Triggers when slider has played
    });
});
</script>

The effect parameter can be any of the following:

random
strip-down-right
strip-down-left
strip-up-right
strip-up-left
strip-up-down
strip-up-down-left
strip-left-right
strip-left-right-down
slide-in-right
slide-in-left
slide-in-up
slide-in-down
left-curtain
right-curtain
top-curtain
bottom-curtain
fade
block-random
block-fade
block-fade-reverse
block-expand
block-expand-reverse
block-expand-random
block-drop-random
zigzag-top
zigzag-bottom
zigzag-grow-top
zigzag-grow-bottom
zigzag-drop-top
zigzag-drop-bottom
strip-left-fade
strip-right-fade
strip-top-fade
strip-bottom-fade

C) The HTML5 "data-" attributes
=====

The URL of the image on the slide is added by using the HTML5 data- attribute. This allows to load the image only when the slideshow calls it and not (lazy load method).

By using the HTML5 data- attribute you can add many properties to your slide, that overwrite the general ones. For instance the URL of the thumbnails:

<div data-iview:thumbnail="photos/photo1_thumb.jpg" data-iview:image="photos/photo1.jpg"></div>
or a transition effect for one slide only:

<div data-iview:image="photos/photo1.jpg" data-iview:transition="zigzag-top"></div>
You can set a random transition between many effects:

<div data-iview:image="photos/photo1.jpg" data-iview:transition="zigzag-top,top-curtain,fade"></div>
Here below you can see all the other "data-" possibilities:

Parameter	Accepted values
=====

data-iview:transition	Transition type can be any one of the following: "strip-down-right", "strip-down-left", "strip-up-right", "strip-up-left", "strip-up-down", "strip-up-down-left", "strip-left-right", "strip-left-right-down", "slide-in-right", "slide-in-left", "slide-in-up", "slide-in-down", "left-curtain", "right-curtain", "top-curtain", "bottom-curtain", "fade", "block-random", "block-fade", "block-fade-reverse", "block-expand", "block-expand-reverse", "block-expand-random", "block-drop-random", "zigzag-top", "zigzag-bottom", "zigzag-grow-top", "zigzag-grow-bottom", "zigzag-drop-top", "zigzag-drop-bottom", "strip-left-fade", "strip-right-fade", "strip-top-fade", "strip-bottom-fade"
data-iview:easing	for the complete list http://jqueryui.com/demos/effect/easing.html
data-iview:image	The URL of the image of the slide
data-iview:thumbnail	The URL of the thumbnail of the slide (if the value of the 'controlNavThumbs' option is true)
data-iview:pausetime	The milliseconds between the end of the sliding effect and the start of the next one
data-iview:type	The type of the slide (set it to video to optimize slider for video show)

D) CSS Styles and Structure
=====

I'm using two CSS files in this sample. The first one contains some general styling, such as anchor tag colors, font-sizes, etc for the page.

The second file contains all of the specific stylings for the script. Keep in mind, that these values might be overridden somewhere else in the file. The file is separated into sections using:

/* The strips and blocks in the Slider */
.iview-strip {
    some styles
}
.iview-block {
    some styles
}
 
/* Direction nav styles (e.g. Next & Prev) */
.iview-directionNav a {
    some styles
}
.iview-prevNav {
    some styles
}
.iview-nextNav {
    some styles
}
 
/* Control nav styles (e.g. 1,2,3...) */
.iview-controlNav {
    some styles
}
.iview-controlNav a {
    some styles
}
.iview-controlNav a img {
    some styles
}
.iview-controlNav a.active {
    some styles
}
 
/* The captions in the Slider */
.iview-caption {
    some styles
}
 
/* The timer in the Slider */
#iview-timer {
    some styles
}
 
#iview-timer div {
    some styles
}
 
/* The Preloader in the Slider */
#iview-preloader {
    some styles
}
#iview-preloader div {
    some styles
}
 
/* The video show in the Slider */
.iview-video-show {
    some styles
}
.iview-video-show .iview-video-container {
    some styles
}
.iview-video-show .iview-video-container a.iview-video-close {
    some styles
}
.iview-video-show .iview-video-container a.iview-video-close:hover {
    some styles
}
 
 
/* The tooltip in the Slider */
#iview-tooltip {
    some styles
}
 
#iview-tooltip div.holder {
    some styles
}
 
#iview-tooltip div.holder div.container {
    some styles
}
 
#iview-tooltip div.holder div.container div {
    some styles
}
 
#iview-tooltip div.holder div.container div img {
    some styles
}

E) JavaScript 
=====

How to pause and play the slider?


$('#slider').trigger('iView:pause'); //Stop the Slider
$('#slider').trigger('iView:play'); //Start the Slider

How to change slide?

$('#slider').trigger('iView:goSlide', [2]); //Go to slide 2

How to next and previous the slider?


$('#slider').trigger('iView:previous'); //Go to previous slide
$('#slider').trigger('iView:next'); //Go to next slide

How to set a random starting slide?

var total = $('#slider').children().length;
var rand = Math.floor(Math.random()*total);
$('#slider').iView({
    startSlide:rand
});
Once again, thank you so much for choosing this script. As I said at the beginning, I'd be glad to help you if you have any questions relating to this script.
