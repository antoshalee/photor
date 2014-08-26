Photor
======
Photor is a minimalistic lightweight jQuery gallery with touch devices support.

[License](LICENSE)

##Browser Support

*Full support:* Chrome, Firefox, Safari, Opera 12+, IE 10+, iOS, Android.

*Partial support:* IE 8—9 (without animations).

##Usage

1. Include `photor.min.js` and `photor.min.css`:

    ```html
    <link href="photor.min.css" rel="stylesheet"> <!-- 1.3 KB in gzip -->
    <script src="photor.min.js"></script> <!-- 6.7 KB in gzip -->
    ```

2. Add some HTML:

    ```html
    <div class="photor">

        <div class="photor__viewport">

            <div class="photor__viewportLayer">

                <!-- Add photos -->
                <img src="images/1.jpg" data-thumb="thumbs/1.jpg">
                <img src="images/2.jpg" data-thumb="thumbs/2.jpg">

            </div>

            <div class="photor__viewportControl">
                <div class="photor__viewportControlPrev"></div>
                <div class="photor__viewportControlNext"></div>
            </div>

        </div>

        <div class="photor__thumbs">
            <div class="photor__thumbsLayer"></div>
        </div>

    </div>
    ```

    Note: `data-href` contains a path to the full size photo.

3. Initialize Photor:

    ```html
    <script>
        var element = document.querySelector('.photor');

        new Photor(element);
    </script>
    ```

    Or initialize with jQuery:

    ```html
    <script>
        $(document).ready(function() {
            $('.photor').photor();
        });
    </script>
    ```


##How to build

1. Make sure you have `nodejs`, `npm` and `grunt-cli` installed;

2. When in your project folder, run

        git clone git@github.com:2gis/photor.git
        cd photor

    to clone this repo into a new subfolder and jump into it;

3. Run

        npm install
        grunt

    to install all dependencies and build Photor;

Optional task `grunt dev` builds Photor as well as starts a web server on port 3000, and runs a _watcher_ that rebuilds the project on file change.

##Configuration

You can specify parameters on initialization.

```js
$('.photor').photor({

    // General options
    current: 0,           // {Number}  Index of start slide
    duration: 300,        // {Number}  Transition duration
    loop: false,          // {Boolean} Loop gallery

    // Handlers
    keyboard: true,       // {Boolean} Initialize keyboard event handlers?

    // Prefixes
    itemPrefix: '_',      // {String}  Prefix for class with slide index (e.g. "_12")
    ieClassPrefix: '_ie', // {String}  Prefix for class with IE version (e.g. "_ie8")

    // Classnames
    control: 'photor__viewportControl',
    next: 'photor__viewportControlNext',
    prev: 'photor__viewportControlPrev',
    thumbs: 'photor__thumbs',
    thumbsLayer: 'photor__thumbsWrap',
    thumb: 'photor__thumbsWrapItem',
    thumbImg: 'photor__thumbsWrapItemImg',
    thumbFrame: 'photor__thumbsWrapFrame',
    viewport: 'photor__viewport',
    layer: 'photor__viewportLayer',
    slide: 'photor__viewportLayerSlide',
    slideImg: 'photor__viewportLayerSlideImg',

    // State modifiers
    _loading: '_loading',       // Photo is loading
    _current: '_current',       // Current slide or thumbnail
    _dragging: '_dragging',     // Dragging in progress
    _disabled: '_disabled',     // Control element is disabled (e.g. left button on first slide)
    _alt: '_alt',               // For photos with an alt attribute
    _single: '_single',         // Gallery contains only one photo
    _animated: '_animated',     // Animation in progress
    _hidden: '_hidden',         // Slide is hidden

    // Algorithm
    _auto: '_auto',             // Photo is larger than viewport
    _center: '_center',         // Photo is smaller than viewport

    // Orientation
    _portrait: '_portrait',     // [image width/image height] < [gallery width/gallery height]
    _landscape: '_landscape',   // [image width/image height] >= [gallery width/gallery height]

    // Thumbs
    _draggable: '_draggable',   // Dragging is allowed for thumbnails

    // Transition callback
    onShow: function(instance) {}

});
```