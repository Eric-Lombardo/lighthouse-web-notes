# w4-d4

* teacher notes below

## viewport units
* the viewport is the total window are rendered by the browser so `1vw` is 1/100th of the size of the width of the viewport
* these are commonly used for typography so that the text scales up/down when the window is resized

## pixels
* these are an absolute measurement but they differ in size across each device. example: pixel on phone vs. pixel on desktop

## EMs
* em units are sized relative to its parent element
* these need an absolute measurement at least once so that when using em it will scale with that measurement
* ems are relative to its immidate parent so nested elements sometimes won't give exactly what you want

## REMs (or root EM)
* are sized relative to the font size of the root element (usually is the HTML element)
* these are relative to the `<html>` font size
* use these as much as you can so you only need to change 1 absolute value for smaller/larger screens

## strategy
1. PX measurement for document level so you can make easy sweeping size changes
2. each module on the page should use REM so it relates to the document absolute measurement
3. h1, h2, p, li shoudl be sized in EM and thus be relative to its module

## responsive design
* mobile > tablet (768px) > laptop (1024px) > desktop
* fluid layout: one that stretched and shrinks to fill the width of the screen
* fixed-width: it has the same width regardless of the size of the screen

## SASS
* SASS is a tool for CSS
* SCSS is the syntax
* filetype is `.scss`

## flexbox
* [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* [flexbox](http://tympanus.net/codrops/css_reference/flexbox/)
* [Flexbugs - Flexbox inconsistencies between browsers](https://github.com/philipwalton/flexbugs)

## design patterns
1. mostly fluid
1. coloumn drop
1. layout shifter (complex to pull off)
1. tiny tweaks
1. off-canvas
* click [here](https://developers.google.com/web/fundamentals/design-and-ux/responsive/patterns) for more details
* you want to choose your breakpoint around your content and design NOT around devices

## Disabling viewport zooming
* back in the day webpages would load on mobile completly zoomed out allowing the user to zoom in when necessary. however since we have mobile versions built and catered to mobile we want to de-activate this feature so that the suer can experience the mobile version of the page
* place this in the head of your HTML:
```html
<meta name='viewport' content='width=device-width, initial-scale=1.0, maximum-scale=1.0' />
```

## media queries
```css
@media only screens and (max-width: 400px) {
  // some css rules
}
```
* `@media` = "at rule"
* `only screens` = "media type" (it can be screens/printers etc.)
* `(max-width)` = media features


## design tools
* click [here](https://web.compass.lighthouselabs.ca/activities/927) for a list of front-end design tools

## side-note
* SPA = single page app

# teacher notes
Responsive Design and SASS
A recap of Responsive Design
We discussed how Responsive Design is a design approach and philosophy:

Adapt to different devices
Avoid making assumptions about viewports
Also consider: different input methods and accessibility
And at the same time it's also a set of specific web development techniques:

The viewport tag
Media queries
CSS units like percentages, em, rem, vh and vw.
Flexbox for layouts that adapt and wrap
Mobile-first
Why start the design process with mobile, and work your way up to larger viewports?

It's valuable to focus on the more constrained environment first, i.e. the smallest viewport.
- It's easier to start with a smaller canvas
Accessibility
Consider not just the screen size, but how your users may be interacting with your page:

What input methods are they using: keyboard and mouse? touchscreen? only keyboard?
Do they need larger text or the ability to zoom in?
Are they using a screen-reader? Consider reading up on web accessibility techniques.
Resources for responsive design techniques
Media queries
Media Queries on MDN
Responsive Design Patterns
MediaQueri.es
Flexbox
A complete guide to flexbox: css-tricks.com
Flexbox.help
Flexbox Froggy
SASS: a CSS preprocessor
SASS is a preprocessor tool, and SCSS is the usual name for the type of CSS format (syntax) that SASS can process.

The most useful features that SASS gives you:

Variables. You define a property value once and re-use it anywhere.
Nesting. You can organize nested CSS better.
Operators. You can calculate values on the fly with arithmetic operators.
Functions like lighten() and darken()
To use SASS as a preprocessor with an express project, a middleware module is available. See node-sass-middleware