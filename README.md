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


Mobile-first Development means *develop for the most basic experience, and then progressively enhance* ... (using Media Queries) towards a full Progressively Enhanced experience.

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

![Mobile-first Twitter](https://github.com/elisechant/mobile-first-sass-tool/blob/master/images/mobile-first-twitter.jpg?raw=true)


To get the stoopid browsers to get a two column layout in desktop viewports you need the **Mobile-first SASS Tool**.

``app-basic.css`` is a stripped-down version of ``app.css``. It keeps only the relevant content for the full desktop experience, stripping away the Media Queries and locks the viewport so these browser can not resize, enabling Developers to practice real Mobile-first without all of the cross-browser headaches, currently IE8< browsers.


## How to use

1 - Define your media queries at _scss/app/_config.scss:Tool
````
$mq-group2: em(600px);
$mq-group3: em(768px);
$mq-group4: em(1024px);
````

2 - Define your minimum Media Query for app-basic at _scss/app/app-basic.scss. Anything less than this value will not be included in the export.
````
$fix-mqs: $mq-group3;   // change this to your minimum media query
````

3 - Only use the Media Query Mixins outlined at _scss/app/_tool.scss. Example usage at _scss/app/_tests/_media-query-parsing.scss
````
.myGeneralExample {
	@include respond-min($mq-group2) {
		content: "General example";             // render something greater than $mq-group2
	}
}

.myAdvancedExample {
	@include respond-min($mq-group2) {

		@include respond-max($mq-group4) {
			content: "Advanced example";        // render something between $mq-group2 and $mq-group4
		}
	}
}
````


## Sample output

![Mobile-first SASS Tool sample output](https://github.com/elisechant/mobile-first-sass-tool/blob/master/images/Screen Shot 2014-05-04 at 10.39.03 am.png?raw=true)

