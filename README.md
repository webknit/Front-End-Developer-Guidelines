Developer-Guidelines
====================

## Categories
### Introduction
These developer guidelines attempt to outline fundamental aspects of the FE development process. They aim to ensure the team is consistent in all the work that we produce. We aim to continuously update the guidelines as new practices and technologies develop, this provides us with an excellent opportunity to stay on top of our game.
While some of the rules in this document are personal preference we have agreed on them in over to ensure we’re all on the same wavelength. If you feel something is missing, inaccurate or incorrect then speak up and make yourself heard!

#### Catering
##### Desktop
By default we develop for current (two previous?) versions of major desktop browsers such Safari, Chrome, Internet Explorer (IE), Firefox and Opera. We also test to ensure IE8 for Windows users get an appropriate, possibly different, experience.
Requests outside of our default specifications need to be discussed and the appropriate timings allocated.

##### Mobile
Testing popular small-screen devices is essential in ensuring that a person’s experience of a design is appropriate to the capabilities of the device they’re using. We test our work in:
- iOS: Safari, Google Chrome and Opera Mini
- Android 4.1: Google Chrome, Firefox and Opera Mini 

### Basics
We use 4 spaces per indentation level. We **never** mix tabs and spaces.


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
- Bad code examples (e.g. <br>)
- Indentation
- Bugfixes for older browsers (e.g. inline block IE7) adding IE stylesheet if needed conditional
- Markup examples
- Assets paths (global folder structure)
- Accessibility overview & tips (alt tags, keyboard presses)
- use of <img> tag (srcset, supplying retina)
- <!DOCTYPE html>
- Clean light might up to ensure good SEO and maintainability
- Use of HTML5
- <strong> and <em> over <b> and <i> as provide strong/emphasised hints to screen reading software
- Overuse of structural markup - cleaner the better, target individual elements
- Cache-busting string
- Use of double quotes
- geolocations


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


## JS & other
- When to use jquery
- Linking jquery (library etc)
- Structure of code (modular, DRY)
- Ajax guidelines
- JS errors debugging
- Using plugins
- minifying js on deployment
- Use of single quotes unless needed in string ("a string that's double quoted”)?
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