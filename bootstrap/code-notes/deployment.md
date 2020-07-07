# Deployment
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

