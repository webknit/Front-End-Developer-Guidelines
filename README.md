Developer-Guidelines
====================

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