# jQuery ScaleText

### Quickly scale text inside a container to be as large as possible without spilling.

* Works on containers, or elements (h1 for example)
  * Recursively checks children for overflow
* Works safely on hidden containers
* Changes no CSS other than font-size
  * Reset the scaling by simply changing the container font-size
* Doesn't require a fixed sized container
  * Measures container and uses that as its basis for scaling
* Creates and maintains relative font sizes within container
  * Pixels/Ems/Percentages etc. all supported
  * Optionally turn this off to support a mixture of fixed and scalable font sizes
* Non-linear progression makes it fast, no matter what container size
  * Fast enough to use in (some) animation environments
  * Reduce accuracy and make it even faster
* No minimum/maximum font size required. Make it FIT.
* Optional vertical middling
* Optional animation
* Chainable (duh!)

Working on projects such as [ThinkWall](http://thinkwall.com), I often need to fit text to a container, so it is the largest font size possible without spilling out, to aid legibility at a distance. Think of full-screen text adverts, or labels on a graph.

This is a fairly specific requirement, and is no replacement for good, responsive layout. 

There are a couple of other solutions out there but most are quick hacks that are slow or restrictive. However, my implementation is fast enough for general use without breaking things - even in animations. 

When choosing your font sizes in a container - think about the relativity of the sizes more than the size itself, as ScaleText will maintain these proportions as it scales, no matter what unit you specify your fonts in.

I've tested in the latest IE/Chrome/FireFox/Android and that's it - sorry. The code is based on core jQuery principles, so it should be fairly compatible. Please let me know if it's not. I have had to change the methodology as I've worked on this code, as there were issues cross-browser, or when zoomed.

If you have any feature requests - drop me a line on [spode@justfdi.com](mailto:spode@justfdi.com) or [@spode](http://twitter.com/spode) on Twitter.

Demo is included in the code, but I've also hosted it on my [personal site](http://spode.me/jquery-scaletext/demo). It may not always be the latest version.

## Usage

1. Include jQuery:

	```html
	<script src="http://ajax.googleapis.com/ajax/libs/jquery/2.0.0/jquery.min.js"></script>
	```

2. Include plugin's code:

	```html
	<script src="dist/jquery.scaletext.min.js"></script>
	```

3. Call the plugin:

	```javascript
	$("#element").scaleText();

	/*or chain it with new settings*/
	$('#element').height("200px").scaleText();
	```

## Options

* verticalMiddle : true

ScrollText will add a spacer element to the top of the container with class "scaleTextSpacer" in order to middle the content, assuming it can't fit 100%

* makeRelative : true

ScaleText finds all containing elements and converts fixed sizes to relative sizes. If you know your fonts are already relative, or you want to have a mixture of fixed and relative font sizes, then turn this option off.

* scaledClass : "scaledText"

This class is added to the container after scaling has taken place.

* animate : false

Animate the change in font-size.

* animateSpacer : true

If animating, should the spacer be animated to? It will increase in height.

* animateOptions : {}

Passthrough of animation options in case you want to change duration / easing etc.

* accuracy : 100

If you decrease this value, the less perfect the fit will be, but the less intensive the scaling is. This is only really useful when doing animations, where every millisecond counts. I believe 0 will give you a tolerance of -10%. Reducing accuracy will *never* leave you with the text overspilling.

* paddingCheckChildren: true

When scaling the contents of your container, this will recursively check any children that are also parents, to make sure our scaling isn't causing any overspill there too. This has quite an effect on performance, increasing the number of checks by magnitudes. You can avoid this by being specific about what you are scaling.

* overflowCheckContainer: true

In some scenarios, you just want to scale the contents of the children as much as you can, and you aren't worried if it causes the main container to increase in size. 

* fixedWidth/fixedHeight : true

By default the container will fix at the size it was called at. Changing these allows expansion in either dimension.

* debug : false

Will output to the console how many iterations it required to scale and how long it took to do so. This is useful if you are tweaking your accuracy.

## Contributing

Check [CONTRIBUTING.md](https://github.com/unclespode/jquery-scaletext/blob/master/CONTRIBUTING.md) for more information.

## History

Check [Releases](https://github.com/unclespode/jquery-scaletext/releases) for detailed changelog.

## License

[MIT License](http://zenorocha.mit-license.org/) © Andrew @Spode Miller
