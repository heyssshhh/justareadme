# GULP WORKSHOP

In this workshop, you will learn how to use gulp to tie together other cool technologies shown in other workshops. We can convert pug into html, sass into css, and deploy easily using gulp!

## Setting up gulp

:rocket: **Run these two commands in your project directory to install gulp:**

`sudo npm install -g gulp`

`npm install --save-dev gulp`

**Open `gulpfile.js`**

:rocket: There's a file called gulpfile.js in your project root. Open it! This is the file we will be working work in.  Let's make sure we can use gulp by finding the tag that says **"//include gulp"** and under that add:

`const gulp = require('gulp');`

Great! First, we'll add in a plugin for sass and Pug that will compile our files into html and css

### SASS

:rocket: Under **"// Include Our Plugins"** add:

`const sass = require('gulp-sass');`

:rocket: Under **"//Compile our sass"** add:

```
gulp.task('sass', () => {
  return gulp.src('src/*.scss')
        .pipe(sass())
        .pipe(gulp.dest('dist/css'));
});
```
:rocket: Now in your terminal, run:

`gulp sass`

This will find our sass file in src folder, compile it and put the resulting css into our destination folder "dist". Okay, now let's compile our Pug file into html!

### PUG

:rocket: Let's go back to  **"// Include Our Plugins"** and add another plugin that will compile your Pug templates into HTML:

`const pug = require('gulp-pug');`

:rocket: Under "//Compile our Pug" add:

```
gulp.task('Pug', () => {
  return gulp.src('src/*.scss')
        .pipe(pug())
        .pipe(gulp.dest('dist'));
});
```
:rocket: Let's compile our Pug! in terminal run:

`gulp pug`

You should see the hmtl file in your 'dist' folder now :)

# Other plugins

Now that you have the hang of things. Lets add some more plugins at once.

:rocket: Under **// Include Our Plugins** add these plugins:
```
const jshint = require('gulp-jshint');
const concat = require('gulp-concat');
const uglify = require('gulp-uglify');
const rename = require('gulp-rename');
const imagemin = require('gulp-imagemin');
const coffee = require('gulp-coffee');
```
jshint is used for linting, rename is for renaming our compiled fires, imagemin is for image compression, uglify and concat is for minimizing and concatinating our js files, and coffee is for converting CoffeeScript into Javascript. Basically, we want to compile and minisize our files and give them a desired name in the destination folder, make our images take up less space,and make sure everything is properly linted.

:rocker: Under **"// Lint Task"** add:
```
gulp.task('lint', () => {
  return gulp.src('src/*.js')
        .pipe(jshint())
        .pipe(jshint.reporter('default'));
});
```
:rocker: Under **"// mininize images"** add:
```
gulp.task('images', () => {
  return gulp.src('src/img/*')
        .pipe(imagemin())
        .pipe(gulp.dest('dist/images'));
});
```
:rocker: Under **"// Compile CoffeeScript,Concatenate & Minify JS"** add:
```
gulp.task('coffee', function() {
  gulp.src('./src/*.coffee')
    .pipe(coffee({bare: true}))
    .pipe(gulp.dest('./public/'));
});

gulp.task('scripts', () => {
  return gulp.src('src/*.js')
        .pipe(concat('all.js'))
        .pipe(gulp.dest('dist'))
        .pipe(rename('all.min.js'))
        .pipe(uglify())
        .pipe(gulp.dest('dist'));
});
```
:rocket: Awesome copying and pasting skills :octocat:.  Now compile by running:
`gulp`

lets test out your code locally by running `njanckjlabaefraevevt`

## FINISHED!
At this point you should have ...
- [ ] Set up gulp
- [ ] added in plugins
- [ ] compiled and minified everything
- [ ] understood how cool gulp is!!
