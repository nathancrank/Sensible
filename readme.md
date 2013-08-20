# Sensible v0.7 beta
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
@include border-box();

To set up the viewport using the new css declarations:
@include viewport();

To quickly set all elements to use border-box and declare the new css declarations use:
@include sens-prep();

### Save Development Time
Sensibles real strength and workflow benefit comes from using the minq(), maxq(), mres() and background-progressive().

minq() and maxq() declare min-width and max-width media queries and print and IE selector with the same styles if it qualifies against the constant $sens-oldie-bp. minvq() and maxvq() declare vertical media queries.

To use minq() and maxq(), first declare the IE conditionals at the top of your sites html above the head tag.

	<!DOCTYPE html>
	<!--[if lt IE 9]> <html class="no-js oldie"> <![endif]-->
	<!--[if IE 9]> <html class="no-js ie9"> <![endif]-->
	<!--[if gt IE 9]><!--> <html class="no-js"> <!--<![endif]-->

There are a few defaults to set in your sass.
$sens-oldie-selector: ".oldie";
$sens-oldie-bp: 60em;

$sens-oldie-selector defines the selector used in your IE conditionals.

$sens-oldie-bp defines the media query at which all styles applied to higher media queries also apply to oldie.
Examples:
- $sens-oldie-bp is set at 60em
- @include minq(32em) {} styles would be applied to oldie, but minq(77em) would not
- @include maxq(32em) {} styles would not be applied to oldeie, but maxq(77em) would be
- @include maxq(32em, true) {} styles would be applied
- @include maxq(117em, false) {} styles would not be applied

mres() lets you pass a basic integer the defines a minimum css pixel ratio at which above to use the included css.
- @include mres(2) would match an Apple retina device.
- @include mres(1.3) would match a Nexus 7
- @include mres(4) would match something awesome thats not out yet.

background-progress() helps you use @2x png/jpg images and svg/webp to provide hires images. It takes advantage of Compass's image-url() feature to make relative paths irrelevant.
- @include background-progressive("test") would print code for a standard 1x png and a 2x png.
- @include background-progressive("test", jpg) would print the same code but for jpgs.
- @include background-progressive("test", svg) would print code for a 1x png and an svg where supported
- @include background-progressive("test", png svg) would print code for a 1x png, a 2x png and an svg
- @include background-progressive("test", png webp svg) would print code a a 1x png, a 2x png, a webp, and an svg
All files should be named the same thing, except with an @2x where appropriate.
ex. test.png, test@2x.png, test.jpg, test@2x.jpg, test.svg, test.png

* SVG & WebP support requires Modernizr or similar testing suite to apply .svg and .webp to <html>.

## Support
You can email me at sensible@nathancrank.com if you have questions.

## License
None, have fun.