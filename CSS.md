# Front End Developer Guidelines

## CSS
CSS is probably the most abused FE development language. It’s vital our CSS is well constructed and neat. 
Some good characteristics of CSS include:-
	- Well structured
	- Neat 
	- Low specificity
	- Modular/reusable

We primarily use SASS to write our CSS but for smaller projects we might want to use vanilla CSS. Both are covered below.

### CSS Basics
- We don’t write inline styles, keep markup and styles separate
- We write our CSS **Mobile first**
- We **avoid** !important rules 
- We use the <link> tag to include, never @import
- We avoid nesting more than 3 deep.
- We keep it DRY! (Don’t repeat yourself)
- We avoid using ID’s as too specific
- We write our CSS alphabetically 
- We use em’s/rems over pxs
- We use # colours unless using rgba

### CSS syntax
We make good use of line breaks, indent and whitespace to make our code neat, readable and maintainable.
Some things to note.
- class name followed by one space
- Open brackets and new line
- One indent (4 spaces)
- Write css alphabetically in the following format, attribute, colons, space, value, colon.
- Close brackets on separate line on same vertical axis that the class started
- Group related CSS properties together (no line breaks)
- Break (two line breaks) and title different modules within the CSS document.

```
/*** SIDEBAR STYLES ***/
.sidebar {
	color: red;
	font-size: 1.2em;
	width: 100%;
}
.sidebar a {
	color: black;
	padding: 2em;
}


/*** MAIN BODY STYLES ***/

.main-body {
	margin: 0 auto;
	width: 80%;
}
.main-body a {
	color: yellow;
}
```

### SASS syntax
Our SASS should mirror the vanilla CSS we write, this means no unnecessary nesting or duplicated styles.

```
/*** SIDEBAR STYLES ***/
.sidebar {
	color: red;
	font-size: 1.2em;
	width: 100%;
	a {
		color: black;
		padding: 2em;
	}
}

/*** MAIN BODY STYLES ***/

.main-body {
	margin: 0 auto;
	width: 80%;
	a {
		color: yellow;
	}
}
```

### Naming convention
As previously mentioned in the HTML section we make use of a naming convention in order to avoid nesting and make our code more modular.

Lats make use of the examples from the HTML naming conversion section and elaborate on how the CSS works with the naming convention.

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

We write the SASS like this.

```
.top-bar {
	background: black;
	width: 100%;
	&- -blue {
		background: blue;
	}
	&__info {
		background: white;
		float: left;
		&- - right {
			float: right;
		}
	}
}
```

Which outputs (Remembers If you’re writing CSS then this is how it should look)

```
.top-bar {
	background: black;
	width: 100%;
}

.top-bar- - blue {
	background; blue;
}

.top-bar__info {
	background: white;
	float: left;
}

.top-bar__info- - right {
	float: right;
}
```

Notice how all of these rules are only one level deep. Nesting is avoided when making use of a naming convention. Elements such as a, ul, li, p etc can be nested two deep so that they overwrite the base styles. However it should be ensured that they’re only two levels deep, consider the following example.

```
.sidebar {
	li{
		a {
			color: red;
		}
	}
}
```

There’s absolutely no need lo have the a nested inside the li.

```
.sidebar {
	li{
	}
	a {
		color: red;
	}	
}
```

Smarter and cleaner CSS results is an improvement for end users and developers.

### Sizing
We make use of ems for our sizing attributes as it means that we have great control over the elements of our websites. It’s also better for accessibility ensuring users can zoom correctly.

TO BE COMPLETED

### SASS modules/Partials
SASS is great as it allows us to split our code up into smaller chunks before it’s compiled into one stylesheet. Both modules & partials are in their own folders and pulled in via a main SASS index file (style.scss).
Basic modules and partials are defined in boilerplates, but think ahead and plan how they could be best used on your project.

#### Modules
The modules directory is reserved for Sass code that doesn't cause Sass to actually output CSS. Things like mixin declarations, functions, and variables.

- _variables.scss - Colours, Gradients, Typography
- _functions.scss - All the functions go in here
- _mixins.scss - All the mixins go in here
- _vendor.scss - The vendor directory is for third-party CSS

#### Partials
The partials directory is where most of the CSS is constructed.

- _reset.scss - Reset, including HTML5
- _base.scss - All the base elements, HTML, body, container, headers, links, img, blockquote etc
- _buttons.scss - Button styles
- _forms.scss - Form styles
- _font-face.scss - Font face stuff


#### style.scss
The main stylesheet imports the modules and partials to make the CSS document. Try make use of titles in order to see what’s going on in all SASS documents. Remember the partials might be dependant on the mixins, so ensure they’re in the right order.

```
/*** MIXINS ***/
@import "modules/_mixins";

/*** BUTTONS ***/
@import “partials/_buttons”;

/*** SIDEBAR ***/
@import “partials/_sidebar”;
```

### Media queries/BG images support
Rather than splitting our media queries up into other stylesheets we make use of a SASS mixin to do the hard work for us.

#### Media queries
```
/*** 
Example mixin file | This would be in the mixins folder 
***/
@mixin breakpoint($point) {
		@if $point == medium {
			@media only screen and (min-width: 50em) { @content; }
		}
		@else if $point == large {
			@media only screen and (min-width: 73.125em) { @content; }
		}
}

/*** The we nest the media queries as follows ***/
.sidebar {
	width: 100%;
	@include breakpoint(medium) {
		float: right;
		width: 30%;
	}
}

/*** Which outputs ***/
.sidebar {
	width: 100%;
}
@media only screen and (min-width: 50em) { 
	.sidebar {
		float: right;
		width: 30%;
	}
}

```

I mentioned before about finding a balance between performance and maintainability. This method outputs dozens of media queries rather than nesting all rules in one. However research shows that there is no significant different between the two methods and this method is far far more maintainable.

#### BG images
Standard BG image support is as follows
```
.icon {
	background: url(assets.icon.png) no-repeat;
	height: 10px;
	width: 10px;
}
```
BG support for retina works like this
```
/*** 
Example mixin file | This would be in the mixins folder 
***/
@mixin breakpoint($point) {
		@else if $point == retina {
			@media print, (-o-min-device-pixel-ratio: 5/4), (-webkit-min-device-pixel-ratio: 1.25), (min-resolution: 120dpi) { @content; }
		}
}

/*** Example SASS ***/
.icon {
	background: url(assets/icon.png) no-repeat;
	height: 10px;
	width: 10px;
	@include breakpoint(retina) {
		background: url(assets/icon@2x.png) no-repeat;
		background-size: 10px 10px;
	}
}

/*** Outputs ***/
.icon {
	background: url(assets/icon.png) no-repeat;
	height: 10px;
	width: 10px;
}
@media print, (-o-min-device-pixel-ratio: 5/4), (-webkit-min-device-pixel-ratio: 1.25), (min-resolution: 120dpi) {
	.icon {
		background: url(assets/icon@2x.png) no-repeat;
		background-size: 10px 10px;
	} 
}
```

Remember that this is adopting a **mobile first/progressive enhancement** approach. Our mobile styles being replaced by more styles as the viewport gets larger.

BG images are great but they have their limitations. As technology continues to improve so too will the quality of their screens, it won’t be long before a 3x image will need to be served by default. See the next section for bulletproof retina images regardless of the resolution.

#### Sprites
Each image that’s loaded into the browser requires a http request. The more http requests we have the slowest he webpage will load. Instead of having dozens of small image files consider combining them into one image and making use of the CSS background-position property.

```
/*** 
Example mixin file | This would be in the mixins folder 
***/
@mixin breakpoint($point) {
		@else if $point == retina {
			@media print, (-o-min-device-pixel-ratio: 5/4), (-webkit-min-device-pixel-ratio: 1.25), (min-resolution: 120dpi) { @content; }
		}
}

/*** Example SASS ***/
.icon {
	background-image: url(assets/sprite.png);
	background-position: 50px 40px;
	height: 10px;
	width: 10px;
	@include breakpoint(retina) {
		background: url(assets/sprite@2x.png) no-repeat;
		background-size: 500px 500px;
	}
}

/*** Outputs ***/
.icon {
	background-image: url(assets/icon.png);
	background-position: 50px 40px;
	height: 10px;
	width: 10px;
}
@media print, (-o-min-device-pixel-ratio: 5/4), (-webkit-min-device-pixel-ratio: 1.25), (min-resolution: 120dpi) {
	.icon {
		background-image: url(assets/icon@2x.png) no-repeat;
		background-size: 500px 500px;
	} 
}
```
You can make great use out of compass and websites like sprite cow to find the background position of the images.

### SVG’s
Vectors are massively underrated. They are perfect for retina devices as the scale up and down perfectly **and** their file size is tiny.
They can be used as both foreground and background images in exactly the same was as a jpg or png would.

### Smart CSS

#### Peseudo elements
We make use of peseudo elements to add extra to our websites without having to create extra markup. A good example is the point on a speech bubble. Here’s how we could approach that.

```
.speech-bubble {
	border: 1px solid black;
	border-radius: 5px;
	padding: 20px;
	position: relative;
	&:before {
		background-image: url(assets/speech-point.png);
		bottom: 0px;
		content: “”;
		display: block;
		height: 10px;
		left: -10px;
		position: absolute:
		width: 10px;
	}
}
```
Less markup, neater, cleaner and smart!


#### Specificity
As previously mentioned we should never nest lower than three levels. Using BEM properly means that most CSS will never be lower than 2 levels deep. 

Reset and base styles come first and then onto the site styles. We should avoid using **!important** at all costs, if you find yourself having to use it, or you’re nesting too deep then your markup or css is fundamentally wrong.

#### Smart class names using BEM
If a button, header or any element appears more then once then define it as a global class. Think smart and make use of extra classes using BEM to avoid duplicating styles. Lets look at an example

```
.btn {
	background: red;
	color: white;
	display: inline-block;
	padding: 10px;
}

.btn- -white {
	background: white;
	color: black;
}

<a class=“btn btn- -white”>Click me</a>
```

.btn contains the structure for the button and we simple add the  btn- - white to change the background colour.

#### Prefixing
Standard CSS rules come first and then prefixed ones after

```
.btn {
	transform: opacity 1s ease;
	-webkit-transform: opacity 1s ease;
	-moz-transform: opacity 1s ease;
	-o-transform: opacity 1s ease;
}
```

We can also use compass to sort these for us.