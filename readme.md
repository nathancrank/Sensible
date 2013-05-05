# Sensible v0.5
A Mobile-First Responsive Design SCSS framework
Nathan Crank

## What is Sensible?
Sensible makes it easy to design responsive, mobile-first websites that still work in IE well. It is a collection of SCSS mixins designed to make mobile-first design easier.

## Requirements
SASS. But you're already using that, right?

## Use
### Getting started Sensibly
To get started, Sensible can set a few intelligent defaults that make responsive design easier.

To set an element to use border-box:
@include sens-border-box;

To set up the viewport using the new css declarations:
@include sens-viewport;

To quickly set all elements to use border-box and declare the new css declarations use:
@include sens-prep;

### Save Development Time
Sensibles real strength and workflow benefit comes from using the minq(), maxq(), mres() and sens-bg-image().

minq() and maxq() declare min-width and max-width media queries and print and IE selector with the same styles if it qualifies against the constant $sens-oldie-bp. 

To use minq() and maxq(), first declare the IE conditionals at the top of your sites html above the <head> tag.

<!DOCTYPE html>
<!--[if lt IE 9]> <html class="no-js oldie"> <![endif]-->
<!--[if IE 9]> <html class="no-js ie9"> <![endif]-->
<!--[if gt IE 9]><!--> <html class="no-js"> <!--<![endif]-->

There are a few defaults to set in your sass.
$sens-oldie-selector: ".oldie";
$sens-oldie-default: false;
$sens-oldie-bp: 60em;

$sens-oldie-selector defines the selector used in your IE conditionals.

$sens-oldie-default toggles whether all calls of minq() and maxq() print and IE selector. It is set to false by default (and I recommend you leave it that way)

$sens-oldie-bp defines the media query at which all styles applied to higher media queries also apply to oldie.
Examples:
- $sens-oldie-bp is set at 60em
- @include minq(32em) {} styles would be applied to oldie, but minq(77em) would not
- @include maxq(32em) {} styles would not be applied to oldeie, but maxq(77em) would be
- @include maxq(32em,true) {} styles would be applied

mres() lets you pass a basic integer the defines a minimum css pixel ratio at which above to use the included css.
- @include mres(2) would match an Apple retina device.
- @include mres(1.3) would match a Nexus 7
- @include mres(4) would match something awesome thats not out yet.

sens-bg-image() lets you quickly declare all responsive forms of an image.
Calling:
	@include sens-bg-image($img: "default", $ext: "png", $svg: "true", $hires: "@2x", $hiresmin: "1.1")
Prints:
	background-image: url("default.png");
	@media (-webkit-min-device-pixel-ratio: 1.1), (min-resolution: 1.1dppx) {
		background-image: url("default@2x.png");
	}
	.svg & {
  	background-image: url("default.svg")
	}


*** SVG support requires Modernizr or similar testing suite to apply .svg to <html>.

## Support
You can email me at sensible@nathancrank.com if you have questions.

## License
None, have fun.