# Front-End Web UI Frameworks and Tools: Bootstrap 4
1. [Three-tier Architecture](#three-tier-architecture)
2. [Import BootStrap](#import-bootstrap)
3. [Foundation for Responsive Design](#foundation-for-responsive-design)
4. [Viewport](#viewport)
5. [Grid System](#grid-system)
6. [Media Queries](#media-queries)
7. [jQuery](#jquery)
8. [CSS Preprocessors](#css-preprocessors)
9. [Deployment Check](#deployment-check)
10. [Task Runners](#task-runners)
11. [Bootstrap Codes](https://github.com/vanessaaleung/full-stack-notes/tree/master/bootstrap/code-notes)

## Three-tier Architecture
*   Presentation Layer
    *   UI related issues
*   Business Logic Layer
    *   Data validation, dynamic content processing
*   Data Access Layer
    *   Data persistence, data access through APIs

## Import BootStrap
*   CSS on top, JS on the bottom
*   Want CSS load immediately so that as the page starts rendering
*   JS will take a little bit of time
*   Don’t want users to wait for entire page to be loaded before they see something in the browser

## Foundation for Responsive Design
*   Grid System
*   Fluid Images
*   Media Queries

## Viewport
```html
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
```
Ensures the screen width is set to the device width and the content is rendered with this width in mide

## [Grid System](https://getbootstrap.com/docs/4.5/layout/grid/)
### Flexbox Layout
*   Handle dynamic/unknown size of content containers
*   Direction-agnostic layout
*   Easy vertical alignment of content within a parent element
*   Easy reordering of content across devices with media queries
*   Easy design container to be equal height columns

*   Five classes
    *   default: target all sizes
    *   col-: extra small
    *   sm: small
    *   md: medium
    *   lg: large
    *   xl: extra large
*   Each row is divided into 12 columns
    *   All of the 12 columns will automatically adjust itself to the width that is allowed for the content
*   Specify how many columns each piece of content will occupy within a row, all adding up to 12
```css
.col-*, .col-sm-*, etc.
```

### Auto-Layout Columns

### Vertical Alignment
```html
<div class="row align-item-center">
```

### Horizontal Alignment
```html
<div class="row justify-content-center">
```
*   col-auto: the number of columns the div occupies will be automatically determined by the content

### Column Offsets
```html
<div class="col-sm-4 offset-sm-1">
```
Example: shift 1 column right

### Nesting Columns

## Media Queries
_Apply styles based on the size of the viewport_
```css
@media (min-width:992px) {
	/* Customized CSS styles /*
}
```

## jQuery
_A lightweight Javascript library_
*   Bootstrap JS is built on jQuery

### Syntax
```jquery
$(selector).action()
```
*   $: define/access jQuery
*   (selector): find HTML element

## CSS Preprocessors
*   Less: @ sign
*   Sass (Syntactically Awesome Style Sheets): $ sign
*   Scss (Sassy CSS)
*   Stylus
*   Are compiled into traditional CSS syntax automatically before use in a web page

### Variables
- Less: 
```less
@lt-gray: #ddd;
```
- Scss:
```scss
$lt-gray: #ddd;
```
### Nesting
- Less:
```less
.carousel {
	background:@background-dark;
}
```
- Scss:
```less
.carousel {
	background:$background-dark;
}
```

### Mixins
- Less:
```less
.zero-margin{
	...
}
.row-content {
	.zero-margin;
	...
}
```
- Scss:
```scss
@mixin zero-margin{
	...
}
.row-content {
	@include zero-margin;
	...
}
```

### Mixins with Parameters
- Less: need to initialize parameters
```less
.zero-margin (@pad-up-dn: 0px) {
	...
}
.row-content {
	.zero-margin(50px, 0px);
	...
}
```
- Scss: no need to initialize parameters
```less
@mixin zero-margin (@pad-up-dn) {
	...
}
.row-content {
	@include zero-margin(50px, 0px);
	...
}
```

### Mathematical Operations
```less
.carousel-item .item-large{
	height: @carousel-item0height * 2;
}
```

## Deployment Check
### CSS Check
*   Compiling Sass/Less into CSS
*   Running Autoprefixer to add any vendor prefixes that are needed
*   Minification: removing unnecessary characters
*   Concatenation of all css files

### CSS prefixes
_Add support for new CSS features before those features are fully supported in all browsers_
*   -webkit-: (Chrome, Safari, newer versions of Opera, almost all iOS browsers including Firefox for iOS; basically, any WebKit based browser)
*   -moz-: (Firefox)
*   -o-: (old pre-WebKit versions of Opera)
*   -ms-: (Internet Explorer and Microsoft Edge)

### Javascript Check
*   JSHint: check for errors
*   Concatenation of all js files
*   Uglification: minification + mangling (reduce local variables to single letters)
*   Rechecking for errors

### Other Check
*   Images: optimize file size
*   Watch: watch for changes in files and automatically rerunning tasks
*   Server and Livereload
*   Testing
*   Building the site for deployment

## Task Runners
_Configure the tasks once and rerun it automatically as needed_
*   Grunt: Configuration over Code
*   Gulp: Code over Configuration
*   Others: Cake, Brunch, Broccoli
*   Build systems for the web

## Bootstrap Codes
1. [Responsive Design and Bootstrap Grid System](https://github.com/vanessaaleung/full-stack-notes/blob/master/bootstrap/code-notes/responsive-design.md)
2. [Bootstrap Components](https://github.com/vanessaaleung/full-stack-notes/blob/master/bootstrap/code-notes/components.md)
3. [Bootstrap and jQuery](https://github.com/vanessaaleung/full-stack-notes/blob/master/bootstrap/code-notes/jquery.md)
4. [CSS Preprocessor](https://github.com/vanessaaleung/full-stack-notes/blob/master/bootstrap/code-notes/css-preprocessor.md)
5. [Deployment](https://github.com/vanessaaleung/full-stack-notes/blob/master/bootstrap/code-notes/deployment.md)
