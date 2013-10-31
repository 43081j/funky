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

License
===

MIT
