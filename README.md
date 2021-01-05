funky.js
===

**funky.js** is a library used to add some funky effects and other transformations to webcam media using WebRTC and CSS filters (aka shaders).

Currently, Firefox does *not* provide full support for the `filter` property whereas Chrome does. For this reason, the Negative and Sepia effects will not function correctly unless using Chrome.

**TODO**

* Add a 'doodle' effect allowing the user to draw on the video
* Add a save-as feature to save a snapshot
* Sprite-like images overlaying the video

Demo
===

A demo is hosted [here](//43081j.github.io/funky/).

Example
===

```html
<div id="funky"></div>
<script src="funky.min.js"></script>
<script type="text/javascript">
	var funk = new funky('funky');
	funk.on('error', function(e) {
		console.log(e);
	});
	// Add a negative effect
	funk.effectNegative(true);
</script>
```

Built-in Effects
===

**funky.js** has several built-in effects which may be used like so:

```javascript
var funk = new funky('container');
funky.effectNegative(true);
```

Where `true` enables the effect and `false` disables it.

* effectNegative
    * add a negative effect to the video
* effectVerticalFlip
    * flip the video vertically
* effectVerticalMirror
    * mirror the video across the y-axis
* effectEdgeDetection
    * basic edge detection
* effectPosterize
    * give a poster-like effect
* effectSepia
    * alter colours to the sepia tone
* effectRandomOffset
    * give a scrambled effect on the pixels
* effectEdgeDetectionAlt
    * a better edge detection algorithm
* effectScanLines
    * introduce scan lines onto the video
* effectRgbshifting
    * Shifts RGB colors to left and right

Custom Effects
===

To create your own effects, simply pass a function to the `draw` event and it will be called every time a draw occurs.

```javascript
var funk = new funky('container');
funk.on('draw', function(image, callback) {
	// do your processing here
});
```

`image` is an `ImageData` instance, you may interact with the pixels directly using `image.data`, which is in the form `[r, g, b, a, r, g, b, a, ...]`.

`callback` **must** be called when you are finished processing the pixels so **funky.js** knows to continue with drawing.

`this` is the **funky.js** instance.

Methods
===

* `on(event, callback)` Hook a callback into an event
* `off(event, callback)` Remove a callback from an event

Events
===

* `draw` Called every time a draw occurs, `(image, callback)` will be passed to your callback
* `error` Called every time an error occurs, `(error)` will be passed which contains an `error.code` property

License
===

MIT
