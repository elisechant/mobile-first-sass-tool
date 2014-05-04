# Mobile-first SASS Tool
**A Boilerplate for Real Mobile-first Development without the cross-browser headaches**


## Overview

The **Mobile-first SASS Tool** outputs two source files ``app.css`` and ``app-basic.css``. Rendering the alternate style sheets like this:

````
<!--[if (gte IE 9) | !(IE)]><!-->
	<link rel="stylesheet" href="css/app.css">
<!--<![endif]-->
<!--[if (lte IE 8)]><!-->
	<link rel="stylesheet" href="css/app-basic.css" >
<!--<![endif]-->
````


Mobile-first Development means develop for the most basic experience, and then progressively enhance using Media Queries towards a full Progressively Enhanced experience.

This is the problem with Mobile-first:

````
.container {
	.container__column {
		width: 100%;    // basic experience, column is full width
    	display: block;
	}

	@media screen and (min-width: 600px) {
		@include clearfix;

    	.container__column {
    		width: 50%;     // progressively enhance, 2 columns per container
    		display: inline-block;
    		float: left;
    	}
	}
}
````

With Real Mobile-first Twitter might look like this might look like this in IE8:

![Mobile-first Twitter](https://github.com/elisechant/mobile-first-sass-tool/images/mobile-first-twitter.jpg)


To get the stoopid browsers to get a two column layout in desktop viewports you need the **Mobile-first SASS Tool**.

``app-basic.css`` is a stripped-down version of ``app.css``. It keeps only the relevant content for the full desktop experience, stripping away the Media Queries and locks the viewport so these browser can not resize, enabling Developers to practice real Mobile-first without all of the cross-browser headaches, currently IE8< browsers.


## How to use

todo
