---
title:  "Responsive Images"
---

[Treehouse](http://teamtreehouse.com) has a good video on using HTML5 to create responsive images.  This post is my notes from the course with links to resources that will be useful.  The link to the course is

[Picturefill](http://scottjehl.github.io/picturefill/) is a JavaScript that provides HTML5 support for these techniques in browsers that do not support it.

	<script src="js/picturefill.min.js" async></script>

The async attribute allows for loading of the .js whenever it fits with the browser.  It does not work when there are dependencies such as when jQuery is required for a script.


	<div class="profile-image">
		<img
			srcset="img/photo-@2x.jpg 2x,
				img/photo-@1x.jpg 1x"
			src="img/photo-@1x.jpg"
			alt="Photograph of a flower."
		/>
	</div>

The src is there for a fallback in case the polyfill does not work.  

This is a banner with width descriptor.


	<img
		srcset="img/banner-large.jpg 2040w,
			img/banner-medium.jpg 1400w,
			img/banner-small.jpg 800w"
		src="img/banner-medium.jpg"
		alt="Photograph of Nick Pettit in front of trees."
		class="banner-image"
	/>

The picture width is the value of the width attribute of the picture.

'Sizes' attribute takes one or more CSS media conditions and ends with a length.  It tells the browser how much space the image will take up, but does not resize the image.  CSS resizes.


	<img
		sizes="50vw,
			(min-width: 1024px) 512px"
		srcset="img/banner-large.jpg 2040w,
			img/banner-medium.jpg 1400w,
			img/banner-small.jpg 800w"
		src="img/banner-medium.jpg"
		alt="Photograph of Nick Pettit in front of trees."
		class="banner-image"
	/>

This example is a media first approach, so there is a 50vw (view width) placed first in the size attribute.  The MDN [sizes attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#attr-sizes) documentation has more information on how to use the attribute.

Remember: the srcset width is how wide the image is.  The size attribute is how much space the image should take on the page.

Art Direction
=============

Art direction draws attention to the most important part of the image.  It may be different on different size screens.  This can be done with different image crops.  

The picture element is a container used to specify multiple source files for a child image element.  For more information, see the [MDN documentation on the picture element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture).  This is an experimental technology and not well supported yet.

	<picture>
		<source
			media="(orientation: landscape)"
			srcset="img/banner-large.jpg 2048px,
				img/banner-medium.jpg 1400px,
				img/banner-small.jpg 800w"
		/>
		<source
			srcset="img/banner-square-large.jpg 1000px,
				img/banner-square-medium.jpg 800px"
		/>
		<img
			src="img/banner-medium.jpg"
			alt="Photograph of Nick Pettit in front of trees."
			class="banner-image"
		/>
	</picture>
	
The picture element is like an invisible span.  There is no CSS assigned to it.