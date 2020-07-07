# Css Preprocessor
1. [Less](#less)
2. [Scss](#scss)

## Less
1. Add a file called `styles.less`
2. Add the styles
```less
@lt-gray: #ddd;
@background-dark: #512DA8;
@background-light: #9575CD;
@background-pale: #D1C4E9;

// Height variables
@carousel-item-height: 300px;
```
3. Add the mixins
```less
.zero-margin (@pad-up-dn: 0px, @pad-left-right: 0px) {
	margin:0px auto;
	padding: @pad-up-dn @pad-left-right;
}
```
4. install less
```shell
npm install -g less
```

5. Compile the Less file into a CSS file
```shell
lessc styles.less styles.css
```

## Scss
1. Add a file called `styles.scss`
2. Add the styles
```scss
$lt-gray: #ddd;
$background-dark: #512DA8;
$background-light: #9575CD;
$background-pale: #D1C4E9;

// Height variables
$carousel-item-height: 300px;
```
3. Add the mixins
```scss
@mixin zero-margin($pad-up-dn, $pad-left-right) {
	margin:0px auto;
	padding: $pad-up-dn $pad-left-right;
}
```
4. Install `node-scss`
```shell
npm install --save-dev node-sass
```
5. Add the package as a dependency in `package.json`, to enable the compilation of the Scss file into a CSS file
```json
"scripts": {
  "scss": "node-sass -o css/ css/"
 }
```
6. Transform the Scss file to a CSS file
```shell
npm run scss
```
