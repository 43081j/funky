funky.js
===

**funky.js** is a library used to add some funky effects and other transformations to webcam media using WebRTC.

Demo
===

A demo is hosted [here](https://43081j.github.io/funky/).

Example
===

```html
<div id="funky"></div>
<script src="../dist/funky.js"></script>
<script type="text/javascript">
	var funk = new funky('funky');
	funk.on('error', function(e) {
		console.log(e);
	});
	// Add a negative effect
	funk.process(funk.effectNegative);
</script>
```

Built-in Effects
===

**funky.js** has several built-in effects which may be used like so:

```javascript
var funk = new funky('container');
funk.process(funk.effectNegative);
```

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

Custom Effects
===

To create your own effects, simply pass a function to the `process` method and it will be called every time a draw occurs.

```javascript
var funk = new funky('container');
funk.process(function(image, callback) {
	// do your processing here
});
```

`image` is an `ImageData` instance, you may interact with the pixels directly using `image.data`, which is in the form `[r, g, b, a, r, g, b, a, ...]`.

`callback` **must** be called when you are finished processing the pixels so **funky.js** knows to continue with drawing.

License
===

MIT
