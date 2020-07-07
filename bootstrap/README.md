# Bootstrap
1. [Three-tier Architecture](#three-tier-architecture)
2. [Import BootStrap](#import-bootstrap)
3. [Foundation for Responsive Design](#foundation-for-responsive-design)
4. [Viewport](#viewport)
5. [Grid System](#grid-system)
6. [Media Queries](#media-queries)
7. [jQuery](#jquery)
8. [CSS Preprocessors](#css-preprocessors)
9. [Bootstrap Codes](https://github.com/vanessaaleung/full-stack-notes/tree/master/bootstrap/code-notes)

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
```
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
```
.col-*, .col-sm-*, etc.
```

### Auto-Layout Columns

### Vertical Alignment
```
<div class="row align-item-center">
```

### Horizontal Alignment
```
<div class="row justify-content-center">
```
*   col-auto: the number of columns the div occupies will be automatically determined by the content

### Column Offsets
```
<div class="col-sm-4 offset-sm-1">
```
Example: shift 1 column right

### Nesting Columns

## Media Queries
_Apply styles based on the size of the viewport_
```
@media (min-width:992px) {
	/* Customized CSS styles /*
}
```

## jQuery
_A lightweight Javascript library_
*   Bootstrap JS is built on jQuery

### Syntax
```
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
### Nesting
### Mixins
### Mixins with Parameters
### Mathematical Operations

## Bootstrap Codes
1. [Responsive Design and Bootstrap Grid System](https://github.com/vanessaaleung/full-stack-notes/blob/master/bootstrap/code-notes/responsive-design.md)
2. [Bootstrap Components](https://github.com/vanessaaleung/full-stack-notes/blob/master/bootstrap/code-notes/components.md)
3. [Bootstrap and jQuery](https://github.com/vanessaaleung/full-stack-notes/blob/master/bootstrap/code-notes/jquery.md)
4. [CSS Preprocessor](https://github.com/vanessaaleung/full-stack-notes/blob/master/bootstrap/code-notes/css-preprocessor.md)
5. [Deployment](https://github.com/vanessaaleung/full-stack-notes/blob/master/bootstrap/code-notes/deployment.md)
