# Deployment
1. [Watching for Changes and Parallelshell](#watching-for-changes-and-parallelshell)
2. [Cleaning up a Distribution Folder](#cleaning-up-a-distribution-folder)
3. [Copying Fonts](#copying-fonts)
4. [Compressing and Minifying Images](#compressing-and-minifying-images)
5. [Preparing the Distribution Folder](#preparing-the-distribution-folder)

## Watching for Changes and Parallelshell
1. Install `onchange` and `parallelshell` package

Note: `parallelshell@3.0.2` won't work
```shell
npm install --save-dev onchange parallelshell@3.0.1
```
2. Add the two script items to `package.json`
```json
"scripts": {
	"watch:scss": "onchange 'css/*.scss' -- npm run scss",
	"watch:all": "parallelshell 'npm run watch:scss' 'npm run lite'"
}
```
3. update the start script 
```json
"start": "npm run watch:all",
```
## Cleaning up a Distribution Folder
1. Install
```shell
npm install --save-dev rimraf@2.6.2
```
2. Set up the script
```json
"clean": "rimraf dist",
```

## Copying Fonts
1. Install
```shell
npm -g install copyfiles@2.0.0
```
2. Set up the script
```json
"copyfonts": "copyfiles -f node_modules/font-awesome/fonts/* dist/fonts",
```

## Compressing and Minifying Images
1. Install
```shell
sudo npm install -g imagemin-cli@3.0.0 --unsafe-perm=true --allow-root
```
2. Set up the script
```json
"imagemin": "imagemin img/* --out-dir='dist/img'",
```

## Preparing the Distribution Folder
1. Update `.gitignore`
```gitignore
node_modules
dist
```
2. Set up the script
```json
"usemin": "usemin contactus.html -d dist --htmlmin -o dist/contactus.html && usemin aboutus.html -d dist --htmlmin -o dist/aboutus.html && usemin index.html -d dist --htmlmin -o dist/index.html",
"build": "npm run clean && npm run imagemin && npm run copyfonts && npm run usemin"
```
3. Surround the css links inclusion code with:
```html
<!-- build:css css/main.css -->
<link ...>
<!-- endbuild -->
4. Surround the js links inclusion code with:
```html
<!-- build:js js/main.js -->
<script ...></script>
<!-- endbuild -->
```
5. Build the distribution folder
```shell
npm run build
```
