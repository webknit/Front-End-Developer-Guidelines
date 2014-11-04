# Front End Developer Guidelines

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
- Comment as much as possible, they are removed when compiled in JS and CSS. Don’t hesitate to create a readme file for other devs.
- Keep it **DRY** (Don’t repeat yourself).


## Filenames
This applies to images as well as files.

- Use all lowercase names, saves messing about
- Some OS have restrictions on filenames so don’t use any special characters, you should only use the letters a-z, A-Z, the numbers 0-9, hyphens (-) and underscores (_).
- Don’t use any spaces 
- Keep filenames as logical and short as possible.

## FE to BE process
If you’re working on a project that requires some BE work then please ensure that the hangover is sufficient. 

Make the code as well structured as possible splitting reusable sections such as header and footer into separate files instead of duplicating code in multiple files.

If some classes/markup/conent is going to be dynamically generated server side then ensure that code is in place to handled that, in addition to the BE developer being aware of how to work with your code.
Don’t hesitate to document instructions in a Readme file.
