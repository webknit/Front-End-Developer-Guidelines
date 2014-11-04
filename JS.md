# Front End Developer Guidelines

## JS
JS adds the functionality to our websites, it’s the most dangerous language as far as performance is concerned. Bad JS is - potentially - far worse than bad HTML or CSS.

### JS Basics
- Use of single quotes over double unless needed
- JS is loaded before the closing <body> tag, scripts in head where possible
- Always close lines with semi colons
- Write variable names in camelCase
- Functions start with a Capital letter


### JS Syntax
Give special consideration when naming variables, think what they’re being used for and if they will be used elsewhere.

```
//Namespace
var variable = {};

// Constructor
var MoveMe = function() {};

// String
var footballTeam = ‘Man u’;

// Number
var playerAge = 30;

// Boolean
var injured = true;

// Array
var footballTeamArray = [‘arsenal’, ’spurs’, ‘Chelsea’];

// Object
var teamGoalkeeper = {name: ’Shilton’};
```

#### Structure of JS


#### jQuery
jQuery is a fantastic tool which enables a even playing field across all browsers while making code easier to write. It’s relatively small in size but you should **NOT** be loading the jquery library just to hide a div on click. Consider whether you actually need jQuery before you implement it into your website.

Grab Google CDN's jQuery, with a protocol relative URL; fall back to local if offline.

```
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
	<script>window.jQuery || document.write('<script src="assets/js/libs/jquery-1.11.1.min.js"><\/script>')</script>
```

