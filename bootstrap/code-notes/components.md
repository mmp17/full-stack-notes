# Components
1. [Navigation](#navigation)
2. [Icon Font](#icon-font)
3. [Input](#input)


## Navigation
```html
<nav class="navbar navbar-dark navbar-expand-sm bg-primary fixed-top">
    <div class="container">
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#Navbar">
            <span class="navbar-toggler-icon"></span>
        </button>
        <a class="navbar-brand mr-auto" href="#">Ristorante con Fusion</a>
        <div class="collapse navbar-collapse" id="Navbar">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item active"><a class="nav-link" href="#">Home</a></li>
                <li class="nav-item"><a class="nav-link" href="./aboutus.html">About</a></li>
                <li class="nav-item"><a class="nav-link" href="#">Menu</a></li>
                <li class="nav-item"><a class="nav-link" href="#">Contact</a></li>
            </ul>
        </div>
    </div>
</nav>
```
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















