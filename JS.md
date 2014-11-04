# Front End Developer Guidelines

## JS
JS adds the functionality to our websites, it’s the most dangerous language as far as performance is concerned. Bad JS is - potentially - far worse than bad HTML or CSS.

### JS Basics
- Use of single quotes over double unless needed
- JS is loaded before the closing <body> tag, scripts in head where possible
- Always close lines with semi colons
- Write variable names in camelCase
- Namespaces start with a Capital letter
- Mimify JS before deployment
- **NO** inline js.

#### jQuery
jQuery is a fantastic tool which enables a even playing field across all browsers while making code easier to write. It’s relatively small in size but you should **NOT** be loading the jquery library just to hide a div on click. Consider whether you actually need jQuery before you implement it into your website.

Grab Google CDN's jQuery, with a protocol relative URL; fall back to local if offline.

```
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
	<script>window.jQuery || document.write('<script src="assets/js/libs/jquery-1.11.1.min.js"><\/script>')</script>
```

### Syntax
Give special consideration when naming variables, think what they’re being used for and if they will be used elsewhere.
```
//Namespace
var Namespace = {};

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

Make good use of comments & whitespace as code is minified before deployment. If we had to decide we would take readability over file size any day.

```
function callMe (number) {

 // This line add the number to the button
 document.getElementById(‘button’).innerHTML = number;

}
```

If you’re declaring something more than once then it should be inside a variable. Keep your code clean and today and ensure it’s DRY. If you’re duplicating JS then you’re writing it wrong.

```
$(‘.button’).addClass(‘active’);
$(‘.button’).click(callMe);
$(‘.button’).removeClass(‘active’);

// That button class should be declared once
// You could also chain it
var button = $(‘.button’);
button.addClass(‘active’).click(callMe).removeClass(‘active’);
```

#### Debugging
Make use of the console to debug code. make good use of console.log to figure out what’s going on in your code.

```
function callMe (number) {

	console.log(number);
 // This line add the number to the button
 document.getElementById(‘button’).innerHTML = number;

}
```

You could run into problems with browsers that don’t have consoles. If you’re having issues with the console, check it’s working first!

```
if (typeof console !== 'undefined') // Check for console { 	! console.log('Debug message'); } 
```

#### Plugins
There are many fantastic plugins out there and that can assist us when making websites. Be sure to find a plugin and pick what’s best for your project. For smaller JS functionality, such as a popup box, we should be writing our own code.



