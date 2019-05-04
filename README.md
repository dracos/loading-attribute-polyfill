# loading="lazy" attribute polyfill
*Work in progress*

[![MIT license](https://img.shields.io/npm/l/loading-attribute-polyfill.svg 'license badge')](https://opensource.org/licenses/mit-license.php)
[![loading-attribute-polyfill on Npmjs](https://img.shields.io/npm/v/loading-attribute-polyfill.svg 'npm version')][npm]
[![Total downloads ~ Npmjs](https://img.shields.io/npm/dt/loading-attribute-polyfill.svg 'Count of total downloads – NPM')][npm]
[![jsDelivr CDN downloads](https://data.jsdelivr.com/v1/package/npm/loading-attribute-polyfill/badge 'Count of total downloads – jsDelivr')](https://www.jsdelivr.com/package/npm/loading-attribute-polyfill 'loading-attribute polyfill – on jsDelivr')
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
[![XO code style](https://img.shields.io/badge/code_style-XO-5ed9c7.svg)](https://github.com/xojs/xo)

Fast and lightweight vanilla JavaScript polyfill for the native behaviour to load elements right before they enter the viewport. Provides graceful degradation, and is - not just thatfor - SEO friendly. Handles images with srcset and within picture, as well as iframes. loading="lazy" will be a huge improve for todays web performance challenges, so use and polyfill it today!

- Supports the standard loading="lazy" attribute
- Released under the MIT license
- Made in Germany

## Features

*TBD*

## Core concepts

The polyfill was designed with the following concepts kept in mind:

- dependency-free
- Using JavaScript with graceful degradation

## Installation

Just integrate the JavaScript file into your code - et voilà.

You may optionally load via NPM or Bower:

    $ npm install loading-attribute-polyfill
    $ bower install loading-attribute-polyfill

Afterwards you'll need to wrap all of your `<img>` and `<iframe>` HTML tags that you'd like to lazy load (and thatfor added a {{loading="lazy"}} attribute as well) by an `<iframe>` HTML tag:

### Simple image

```html
<noscript class="loading-lazy">
	<img
		src="https://imgplaceholder.com/250x150/fbfbfb/0f0f0f?font-family=OpenSans_Bold&text=img_br_src_br_loading%3D%22lazy%22"
		loading="lazy"
		alt=".."
		width="250"
		height="150"
	/>
</noscript>
```

### Image wrapped in a picture tag

```html
<picture>
	<source
		media="(min-width: 40em)"
		srcset="
			https://imgplaceholder.com/250x150/fbfbfb/0f0f0f?font-family=OpenSans_Bold&text=picture_br_media+1x_br_loading%3D%22lazy%22 1x,
			https://imgplaceholder.com/500x500/fbfbfb/0f0f0f?font-family=OpenSans_Bold&text=picture_br_media+2x_br_loading%3D%22lazy%22 2x
		"
	/>
	<source
		srcset="
			https://imgplaceholder.com/250x150/fbfbfb/0f0f0f?font-family=OpenSans_Bold&text=picture_br_1x_br_loading%3D%22lazy%22 1x,
			https://imgplaceholder.com/500x500/fbfbfb/0f0f0f?font-family=OpenSans_Bold&text=picture_br_2x_br_loading%3D%22lazy%22 2x
		"
	/>
	<noscript class="loading-lazy">
		<img
			src="https://imgplaceholder.com/250x150/fbfbfb/0f0f0f?font-family=OpenSans_Bold&text=picture_br_img+src_br_loading%3D%22lazy%22"
			loading="lazy"
			alt=".."
			width="250"
			height="150"
		/>
	</noscript>
</picture>
```

### Image with `srcset`

```html
<noscript class="loading-lazy">
	<img
		src="https://imgplaceholder.com/250x150/fbfbfb/0f0f0f?font-family=OpenSans_Bold&text=img_br_src_br_loading%3D%22lazy%22"
		srcset="
			https://imgplaceholder.com/1024x400/fbfbfb/0f0f0f?font-family=OpenSans_Bold&text=img_br_srcset+1024w_br_loading%3D%22lazy%22 1024w,
			https://imgplaceholder.com/640x400/fbfbfb/0f0f0f?font-family=OpenSans_Bold&text=img_br_srcset+640w_br_loading%3D%22lazy%22    640w,
			https://imgplaceholder.com/320x320/fbfbfb/0f0f0f?font-family=OpenSans_Bold&text=img_br_srcset+320w_br_loading%3D%22lazy%22    320w
		"
		sizes="(min-width: 36em) 33.3vw, 100vw"
		alt="A rad wolf"
		loading="lazy"
	/>
</noscript>
```

### Iframe

```html
<noscript class="loading-lazy">
	<iframe
		src="https://player.vimeo.com/video/87110435"
		width="320"
		height="180"
		loading="lazy"
	></iframe>
</noscript>
```

## Optional additional dependencies

In case you'd like to support [older versions of Microsoft EDGE, Microsoft Internet Explorer 11 or Apple Safari up to 12.0](https://caniuse.com/#feat=intersectionobserver), you would could (conditionally) load an IntersectionObserver polyfill:

https://www.npmjs.com/package/intersection-observer

Nevertheless this polyfill would still work in those browsers without that other polyfill included, but [this small amount of users]((https://caniuse.com/#feat=intersectionobserver)) wouldn't totally benefit from the lazy loading functionality - we've at least got you partly covered by using the [Microsoft proprietary lazyloading resource hints](https://caniuse.com/#feat=lazyload).

## API

Nothing really, just plug it in, it ~~will~~ should work out of the box.

## Demo

See the polyfill in action either by downloading / forking this repo and have a look at `demo/index.html`, or at the hosted demo: <https://mfranzke.github.io/loading-attribute-polyfill/demo/>

## things to keep in mind

- The demo HTML code is meant to be simple

[npm]: https://npmjs.com/package/loading-attribute-polyfill 'loading="lazy"-attribute polyfill – on NPM'
