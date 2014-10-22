# Developer Guidelines

## Introduction
These developer guidelines attempt to outline fundamental aspects of the FE development process. They aim to ensure the team is consistent in all the work that we produce. We aim to continuously update the guidelines as new practices and technologies develop, this provides us with an excellent opportunity to stay on top of our game.
While some of the rules in this document are personal preference we have agreed on them in over to ensure we’re all on the same wavelength. If you feel something is missing, inaccurate or incorrect then speak up and make yourself heard!

## Catering
### Desktop
By default we develop for current (two previous?) versions of major desktop browsers such Safari, Chrome, Internet Explorer (IE), Firefox and Opera. We also test to ensure IE8 for Windows users get an appropriate, possibly different, experience.
Requests outside of our default specifications need to be discussed and the appropriate timings allocated.

### Mobile
Testing popular small-screen devices is essential in ensuring that a person’s experience of a design is appropriate to the capabilities of the device they’re using. We test our work in:
- iOS: Safari, Google Chrome and Opera Mini
- Android 4.1: Google Chrome, Firefox and Opera Mini 

## Basics
- We use 4 spaces per indentation level. We **never** mix tabs and spaces.
- We keep our content, presentation and behaviour separate.
- We prefer readability over compression, especially with compile tools. 
- We avoid using !important at all times when building from scratch. If you’re having to add that then you need to go back and rework your code. There may be **rare** exceptions when code is out of our control.

## HTML
Our markup should be well presented, semantically correct and generally valid. We should be writing code that is equally as easy for us developers to read as it is the browser.

### HTML Basics
- We make use of <!DOCTYPE html> which is supported in all browsers.
- We use “double” quotes in our HTML
- We use <strong> and <em> over <b> and <i> as provide strong/emphasised hints to screen reading software
- We don’t use any HTML for styling purposes such as <br>
- Initialise advanced UI (Javascrip enabled) with a advanced/js tag. Meaning our default styles cater at a basic level and then more is added to those who support it. Progressive enhancement is key.
- We make our mobile viewport optimisable using the following snippet
 <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">

### Page speed
In additional to neat clean markup, we also need to ensure that our pages are *fast*. In an ideal world our pages should be less than 1MB in weight. However the world isn’t too ideal and with the rise of full width banners and retina screens websites have sacrificed speed for user experience.

> “Did you seriously load 100kb of jQuery UI just so you could animate the fucking background color of a div?“  
	http://motherfuckingwebsite.com/

Whilst the speed of the sites will generally come down to the budget and requirements of the client, it’s important that we adopt some simple tactics to keep the size of web pages down, such as:
- Only add things to a page that’s needed. Theres’s no point loading the whole jQuery library just so that you can change the colour of a div, just use JS. Same goes with fonts, plugins, web templates etc. Anything that is in your code but not being utilised properly is a waste.
- Images should be as small a size as possible without affecting their visual quality. Make use of ‘save for web’ in photoshop. Where possible images should be no higher than 60kb.
- Make use of vectors(svg) where possible. They’re tiny! Font libraries such as Font Awesome can help with that.
- Make use of dns-prefetch to increase the speed of things such as  google analytics, jquery, typeset etc. http://csswizardry.com/2013/01/front-end-performance-for-web-designers-and-front-end-developers

Images and retina support are discussed later in the document.

### HTML5
Where possible we should look to make use of HTML5 markup. However given that we still support IE8 as default we don’t generally use HTML5 as it would require extra code/bloat in order to make it work. If the client requests HTML5 and support for lower browsers then that’s something we need to consider. Here are some solutions.

HTML5 shiv is a HTML5 IE enabling script. It can be downloaded here, and added to our webpages. The conditional tags ensure that it’s only read by non HTML5 supporting browsers (lower than IE9).
https://code.google.com/p/html5shiv/

```
<!--[if lt IE 9]>
<script src="dist/html5shiv.js"></script>
<![endif]-->
```

If for some strange reason we need to support media queries in  < IE8 - E.g for demo purposes client side - we could use something like respond.js with the conditional tags as above.
https://github.com/scottjehl/Respond
**However** this method is not good practice and should only be used upon client request.

### HTML structure
We should write HTML that is semantic and relevant. Making use of BEM to ensure the “meaning” of our markup is clear when a developer reads it.

We can make use of classes and ID’s in order to style our HTML markup. If ID’s are used they should be used properly and completely unique whilst considering any potential specificity issues. In an ideal world we would use classes for styling and ID’s for JS/anchor functionality. Inline style attributes are to be **avoided**.

We should make good use of indenting and whitespace and ‘blocks’ of HTML to ensure our code is easily readable and maintainable. Grouping elements that appear together on the page and introducing whitespace between ‘blocks’ of content. 

```
<div id=“i-am-unique” class=“top-header”>

	<div class=“top-header__user-info”>

		<h1>Joe Bloggs</h1>
		<p>A badass developer</p>

	</div>

</div>

<div class=“main-body”>

	<div class=“main-body__content”>

		<h1>Page title</h1>
		<p>Some text</p>

	</div>
	
	<div class=“main-body__sidebar”>

		<ul>
			<li>list item 1</li>
			<li>list item 2</li>
			<li>list item 3</li>
		</ul>

	</div>

</div>
```

HTML should be kept as clean and light as possible to ensure speed, maintainability. (and good SEO?) Consider the following.

```
<div class=“logo”>

	<img src=“logo.jpg” />

</div>
```

It would be much better to add the class to the image instead. Targeting individual elements means less markup, less css nesting and more efficient code.

```
<img src=“logo.jpg” class=“logo” />
```

### Naming convention
HTML semantics and FE architecture is a difficult task that requires a naming convention in order to ensure that our projects scale well and are maintainable. You can read more about that here.
http://brettjankord.com/2013/03/06/more-thoughts-on-html-class-naming-conventions/

Although there are lots of naming conventions we make use of BEM (block, element, modifier). Theres an excellent post on that here.http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/

In brief
- block - represents the parent
- element - represents a child of the block 
- modifier represents a different state or version of block

Example

```
<div class=“top-bar top-bar- -blue”>

	<div class=“top-bar__info”>

		<h2>Company name</h2>
		<p>Company address</p>

	</div>

	<div class=“top-bar__info top-bar__info- -right”>

		<h2>Company name on the right</h2>
		<p>Company address on the right</p>

	</div>

</div>
```

### Internet Explorer
As previously mentioned we support IE 8 and above. We may go lower than that, depending on the client. IE9 is(generally) ok to develop for, but IE8 and below can be troublesome. Here are some things that should be kept in mind:

- IE8 and lower won’t understand some things such as some CSS, CSS3 and media queries.
- Depending on the client requirements we might need a separate set of styles for IE such as a “fixed” container. These styles should only be loaded when a user needs it (conditional HTML comments).

As previously outlined in the document it is very difficult to make IE8 and lower look the same as more modern browsers. It’s our duty to ensure the client and project managers are aware of this. Most things can be achieved but it means extra work and therefore we need to be allocated more time. Be sure to check with the client how thorough the support needs to be.

### Folder structure
Whilst this is a personal preference. It’s important that all HTML projects are structured the same in order to ensure that it’s easy for us to pick projects up, we are aware of what’s where and so that automation tools such as grunt will always run correctly. Our structure looks like the following (need to check this)

```
index.html
style.css
assets
	js
	SASS
	img
```

Meaning assets in our index.html will point to

```
<img src=“assets/img/logo.jpg” alt=“a logo” />
```

Each project should have a **README.md** file, especially those in Git. This should contain basic information about the project including, but not limited to
- Title and what the project is
- Who is involved in the project (developers, designers etc)
- Set up information for anyone picking the project up
- Any other information that could be useful

Additional items are also included in our development template such as the gemfile and gruntfile. These will be covered in more detail further into the document.
 
### Accessibility
Taken right from W3C website.

> Web accessibility means that people with disabilities can perceive, understand, navigate, and interact with the Web, and that they can contribute to the Web

It’s important that we are aware of the needs of our end users and ensure we are doing what we can to provide equal access and opportunity.

Accessibility could be simply mean increasing a font size so that it’s easily readable, alternately it could be to ensure a website is completely accessible by screen readers. Full accessibility support is time consuming and costly so it’s important that the requirements are outlined at the beginning of a project.

However by default we should have all the ‘Easy checks’ from the  W3C website covered. Please have a read.
http://www.w3.org/WAI/eval/preliminary.html

There are many tools out there to analyse accessibility if more support is required. A popular one is the WAVE Web Accessibility Tool. http://wave.webaim.org/


### Srcset and picture
As discussed before. Images are one of the most problematic issues on the web. It’s tricky to support different resolutions and sizes. 

For background images we can use CSS media queries to serve the correct size image to the browser, they are discussed in the CSS section.
The support for foreground images has been seriously lacking and we’ve all been waiting impatiently for browser companies to invent something.
The Picture element and srcset/sizes attributes seem to be the answer to our prayers. You can read all about them here.
http://shaneprendergast.co.uk/css/srcset-picture/

> Srcset is about letting go of unnecessary control and trusting the browser to do the right thing for the user, with the user. If you must have specific resources with specific layout breakpoints, it's called art-direction. That's what <picture> is for.  
	https://twitter.com/yoavweiss/status/524634209768701952

There is no reason **NOT** to use the above solutions as they’re supported, can work in most browsers with the polyfill mentioned in the post above **AND** most importantly the standard syntax has a fallback for non supporting browsers.

### JS in the HTML
Where possible there should be **NO** JS in the \<head\> of a HTML document. This reduces the effects of delays imposed by script loading on other page components.
Scripts should be concatenated and minified for performance, our grunt set up does that for us on deployment. If you’re using plugins or libraries the same rules still apply, they should be consolidated to save on http requests.

If using jQuery we should look to use a CDN where possible and use a fallback should that not be accessible

	<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
	<script>window.jQuery || document.write('<script src="assets/js/libs/jquery-1.11.1.min.js"><\/script>')</script>

 


- General
	- Browser Support
- HTML
- CSS
- JS
- Grunt / Project setup
- Images
- Testing
- Deployment


## Generic stuff
- Browser support (IE8+?)/ Base stuff
- Filenames
- Testing (checklist)
- 4 spaces == tab
- Process (FE to BE, how should be handed over tempting etc)
- Commenting (good as gets removed when)
- DRY (applies to everything)
- Setting up projects, grunt
- Git and committing code.
- File structure
- Serving fonts
- Source control, committing with git
- Process


## HTML
- MoDuLaR
- ~~Bad code examples (e.g. <br>~~)
- ~~Indentation~~
- ~~Bugfixes for older browsers (e.g. inline block IE7) adding IE stylesheet if needed conditional~~
- ~~Markup examples~~
- ~~Assets paths (global folder structure~~)
- ~~Accessibility overview & tips (alt tags, keyboard presses~~)
- use of <img> tag (srcset, supplying retina)
- ~~<!DOCTYPE html>~~
- ~~Clean light might up to ensure good SEO and maintainability~~
- ~~Use of HTML5~~
- ~~<strong> and <em> over <b> and <i> as provide strong/emphasised hints to screen reading software~~
- ~~Overuse of structural markup - cleaner the better, target individual elements~~
- Cache-busting string
- ~~Use of double quotes~~
- geolocations
- asynchronous loading, avoid loading in head


## CSS
- CSS syntax
		- Spacing
		- Indenting
- Naming convention (BEM?)
- Progressive enhancement
- SASS rules (partials/mixins/compass)
- Using CSS
- Sizing (ems, px, rems?)
- Nesting media queries in SASS
- Variables in SASS(no more than 3 levels deep)
- Using Compass
- Using moderniser
- BG images
- Supporting retina
- Sprites
- #numbers unless using rgba
- Make use of :after where possible
- !important rule
- How modules work
- Controlling Specificity, how it’s measured and how to work it.
- CSS hacks
- prefixing

## JS & other
- When to use jquery
- Linking jquery (library etc)
- Structure of code (modular, DRY)
- Ajax guidelines
- JS errors debugging
- Using plugins
- minifying js on deployment
- Use of single quotes unless needed in string (eg a string with apostrophe)?
- No scripts in head
- Using advanced/js tag for when JS is enabled (progressive enhancement)
- Javascript patterns (namespaces in objects etc)


## Images
- Image sizes, loading times, lazy load
- Sprites, make use of CSS where possible
- Max image sizes.
- Support for Retina


## Deployment
- Mimify
- Compression 
- Gzip


- What would be easiest way of rolling agree changes out?
- Anyone should be able to request anything for change or add something new.
- Try keep it up to date when we all agree something should be added?
- Beneficial for testing, good practices and of course Lee and any new employees.

Examples 
- https://github.com/styleguide/css
- http://tmwagency.github.io/TMW-frontend-guidelines/
- http://cssguidelin.es/
- http://isobar-idev.github.io/code-standards/
- https://developers.google.com/web/fundamentals/resources/styleguide/index?hl=en
- https://developers.google.com/web/fundamentals/principles/

- JS code - http://javascript.crockford.com/code.html