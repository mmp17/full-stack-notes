# Deployment
1. [Watching for Changes and Parallelshell](#watching-for-changes-and-parallelshell)
2. [Cleaning up a Distribution Folder](#cleaning-up-a-distribution-folder)
3. [Copying Fonts](#copying-fonts)
4. [Compressing and Minifying Images](#compressing-and-minifying-images)
5. [Preparing the Distribution Folder](#preparing-the-distribution-folder)
6. [Grunt](#grunt)

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

## Grunt
1. Install grunt-cli & grunt
```shell
sudo npm install -g grunt-cli
```
```shell
npm install grunt
```
2. Create a Grunt File `Gruntfile.js` and Add the following code
```javascript
'use strict';

module.exports = function (grunt) {
  // Define the configuration for all the tasks
  grunt.initConfig({

  });
};
```
3. Compile SCSS to CSS
- `grunt-sass`: for SCSS to CSS conversion
- `time-grunt`: generates time statistics about how much time each task consumes
- `jit-grunt`: enables us to include the necessary downloaded Grunt modules when needed
```shell
npm install grunt-sass@2.1.0 --save-dev
npm install time-grunt@1.4.0 --save-dev
npm install jit-grunt@0.10.0 --save-dev
```
4. Configure the SASS task in the Gruntfile
```javascsript
'use strict';

module.exports = function (grunt) {
    // Time how long tasks take. Can help when optimizing build times
    require('time-grunt')(grunt);

    // Automatically load required Grunt tasks
    require('jit-grunt')(grunt);

    // Define the configuration for all the tasks
    grunt.initConfig({
        sass: {
            dist: {
                files: {
                    'css/styles.css': 'css/styles.scss'
                }
            }
        }
    });

    grunt.registerTask('css', ['sass']);

};
```
5. Run the grunt SASS task
```shell
grunt css
```
6. Watch and Serve Tasks
*Use the Grunt modules watch and browser-sync to spin up a web server and keep a watch on the files and automatically reload the browser when any of the watched files are updated*
- install the modules
```shell
npm install grunt-contrib-watch@1.0.0 --save-dev
npm install grunt-browser-sync@2.2.0 --save-dev
```
- configure the browser-sync and watch tasks in the Grunt file
```javascript
,
	watch: {
	    files: 'css/*.scss',
	    tasks: ['sass']
	},
	browserSync: {
	    dev: {
		bsFiles: {
		    src : [
			'css/*.css',
			'*.html',
			'js/*.js'
		    ]
		},
		options: {
		    watchTask: true,
		    server: {
			baseDir: "./"
		    }
		}
	    }
	}
```
- Add following task to the Grunt file
```javascript
grunt.registerTask('default', ['browserSync', 'watch']);
```
- Run
```shell
grunt
```

