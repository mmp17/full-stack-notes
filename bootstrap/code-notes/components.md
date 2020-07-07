# Components
1. [Navigation](#navigation)
2. [Icon Font](#icon-font)
3. [User Input](#input)
4. [Tables and Cards](#tables-and-cards)
5. [Images and Media](#images-and-media)
6. [Badges](#badges)
7. [Tabs](#tabs)
8. [Accordion](#accordion)
9. [Tooltips and Modals](#tooltips-and-modals)
10. [Carousels](#carousels)

## Navigation
1. Collapse on small size screen
```html
<nav class="navbar navbar-expand-sm">
```

2. Fix navigation bar on the top when scrolling
```html
<nav class="navbar fixed-top">
`
3. Display the logo/name of the website
```html
<a class="navbar-brand" href="#">
```
4. Push item in the navigation bar to the left
```html
<ul class="navbar-nav mr-auto">
```
5. Display items (pages) horizontally
```html
<li class="nav-item">
```
6. Highlight specific page
```html
<li class="nav-item active">
```
7. Toggler - collapse for shorter screens
```html
<button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#Navbar">
    <span class="navbar-toggler-icon"></span>
</button>
<div class="collapse navbar-collapse" id="Navbar">
    <ul>
    ...
    </ul>
</div>
```
8. Add breamcrumb
```html
<ol class="col-12 breadcrumb">
    <li class="breadcrumb-item"><a href="./index.html">Home</a></li>
    <li class="breadcrumb-item active">About Us</li>
</ol>
```

## Icon Font
1. Install `font-awesome` and `bootstrap-social`
2. Import 
```html
<link rel="stylesheet" href="node_modules/font-awesome/css/font-awesome.min.css">
<link rel="stylesheet" href="node_modules/bootstrap-social/bootstrap-social.css">
```
3. Add icons - use either `<span>` or `<i>`
```html
<span class="fa fa-home fa-lg"></span>
```
```html
<i class="fa fa-phone fa-lg"></i>
```
4. Apply bootstrap social button class
```html
<a class="btn btn-social-icon btn-google" href="#"><i class=""></i></a>
```

## Input
### Buttons
1. Create a button group
```html
<div class="btn-group" role="group">
```
2. Add buttons using `<a>` tag
```html
<a role="button" class="btn"></a>
```
### Forms
1. Add a form
```html
<form>
    <div class="form-group row">
    ...
    </div>
    ...
</form>
```
2. Add inputs inside each row
```html
<label for="lastname" class="col-md-2 col-form-label">Last Name</label>
<div class="col-md-10">
    <input type="text" class="form-control" id="lastname" name="lastname"
        placeholder="Last Name">
</div>
```
3. Add checkbox
```html
<input type="checkbox" class="form-check-input" name="approve" id="approve" value="">
<label class="form-check-label" for="approve">
    <strong>May we contact you?</strong>
</label>

4. Add select
```html
 <select class="form-control">
    <option>Tel.</option>
    <option>Email</option>
</select>
```
5. Add submit button
```html
<button type="submit" class="btn btn-primary">
    Send Feedback
</button>
```

## Tables and Cards
### Tables
1.  Responsive table
```html
<div class="table-responsive">
```

2. Different colors for alternate rows
```html
<table class="table table-striped">
```

3. Dark color for the header
```html
<thead class="thead-dark">
```

### Cards
1. Add a card
```html
<div class="card">
    <h3 class="card-header">Facts At a Glance</h3>
    <div class="card-body">
    ...
    </div>
</div>
```
2. Display information using `<dl>` description list
```html
<div class="card-body">
    <dl  class="row">
        <dt class="col-6">Started</dt>
        <dd class="col-6">3 Feb. 2013</dd>
    </dl>
</div>
```
3. Add a blockquote

`mb-0`: bottom margin is zero
```html
<blockquote class="blockquote">
    <p class="mb-0"></p>
    <footer class="blockquote-footer">Yogi Berra, 
        <cite title="Source Title">The Wit and Wisdom of 
            Yogi Berra, P. Pepe, Diversion Books, 2014</cite>
    </footer>
</blockquote>
```

## Images and Media
### Images
1. Add a image

`img-fluid`: image will automatically be responsive and adapt to the screen size 
```html
<img src="img/logo.png" class="img-fluid">
```
### Media
1. Add a media
```html
<div class="media">
    <img class="d-flex mr-3 img-thumbnail align-self-center" src="img/uthappizza.png" alt="uthappizza">
    <div class="media-body">
        <h2 class="mt-0">...</h2>
    </div>
</div>
```

## Badges
1. Add a red badge
```html
<span class="badge badge-danger">HOT</span>
```

2. Add a secondary badge
```html
<span class="badge badge-pill badge-secondary">$4.99</span>
```
## Tabs
1. Add a tab
```html
<ul class="nav nav-tabs">
  <li class="nav-item">
      <a class="nav-link active" href="#peter" role="tab" data-toggle="tab">Peter Pan, CEO</a>
  </li>  
</ul>
```

2. Add tab contents

- `fade`: animation that allows contents to fade in
- `show`: the content should be shown when the page is rendered, only apply to the first tab
- `active`: the tab should be shown when the page is rendered, only apply to the first tab

```html
<div class="tab-content">
    <div role="tabpanel" class="tab-pane fade show active" id="peter">
```

## Accordion
1. Add a card
```html
<div id="accordion">
    <div class="card">
        <div class="card-header" role="tab" id="peterhead">
        <h3 class="mb-0">
            <a data-toggle="collapse" data-target="#peter">Peter Pan</a>
        </h3>
        </div>
        <div class="collapse show" id="peter" data-parent="#accordion">
            <div class="card-body">
                <p class="d-none d-sm-block">. . .</p>
            </div>
        </div>
    </div>
</div>
```
## Tooltips and Modals
### Tooltips
1. Tooltip over a button

- `data-html="true"`: the tooltip can be styled using html
- `title`: the content of the tooltip
- `data-placement="bottom"`: the tooltip will be displayed to the bottom of the button

```html
<a role="button" class="btn btn-warning btn-reserve btn-sm" 
    href="#reserveForm" data-toggle="tooltip" data-html="true" 
    title="Or Call us at <br/><strong>+852 12345678</strong>"
    data-placement="bottom">Reserve Table</a>
```
2. Add a script (jQuery syntax) to enable the tooltip
```html
<script>
    $(document).ready(function() {
        $('[data-toggle="tooltip"]').tooltip();
    })
</script>
```

### Modals
1. Add a link that could trigger the modal
```html
<span class="navbar-text">
    <a data-toggle="modal" data-target="#loginModal">
        <span class="fa fa-sign-in"></span> Login
    </a>
</span>
```

2. Add a modal

- `data-dismiss="modal"`: when clicks the button, dismiss the modal
```html
<div id="loginModal" class="modal fade" role="dialog">
    <div class="modal-dialog modal-lg" role="content">
        <div class="modal-content">
            <div class="modal-header">
                <h4 class="modal-title">Login</h4>
                <button type="button" class="close" data-dismiss="modal">&times;</button>
            </div>
            <div class="modal-body">

            </div>
        </div>
    </div>
</div>
```
## Carousels
1. Add a carousel
```html
<div class="row row-content">
    <div class="col">
        <div id="mycarousel" class="carousel slide" data-ride="carousel">

        </div>
    </div>
</div>
```

2.  Add carousel content
```html
<div class="carousel-inner" role="listbox">
   <div class="carousel-item active">
        <img class="d-block img-fluid" src="img/uthappizza.png" alt="uthappizza">
        <div class="carousel-caption d-none d-md-block">
            ...
        </div>
    </div>
</div>
```
3. Add styling to properly render the carousel
```css
.carousel-item {
  height: 300px;
}

.carousel-item img {
  position: absolute;
  top: 0;
  left: 0;
  min-height: 300px;
}
```
4. Add slide indicator  
```html
<ol class="carousel-indicators">
    <li data-target="#mycarousel" data-slide-to="0" class="Active"></li>
    <li data-target="#mycarousel" data-slide-to="1"></li>
    <li data-target="#mycarousel" data-slide-to="2"></li>
</ol>
```

5. Add carousel manual control
```html
<a class="carousel-control-prev" href="#mycarousel" role="button" data-slide="prev">
    <span class="carousel-control-prev-icon"></span>
</a>
<a class="carousel-control-next" href="#mycarousel" role="button" data-slide="next">
    <span class="carousel-control-next-icon"></span>
</a>
```



