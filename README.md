# gulp-inline-source

> Inline all `<script>` or `<link>` tags that contain the `inline` attribute with [inline-source](https://github.com/popeindustries/inline-source).

## How it works

`/path/to/file.html`:
```html
<html>
  <head>
    <script src="javascript.js" inline></script>
  </head>
  <body>
  </body>
</html>
```

`javascript.js`:
```js
function test() {
  var foo = 'lorem ipsum';
  return foo;
}
```

Output:
```html
<html>
  <head>
    <script>function test(){var a="lorem ipsum";return a}</script>
  </head>
  <body>
  </body>
</html>
```

## Install

```bash
$ npm install gulp-inline-source --save-dev
```

## Usage

```javascript
var gulp = require('gulp');
var inlinesource = require('gulp-inline-source');

gulp.task('inlinesource', function () {
    return gulp.src('./src/*.html')
        .pipe(inlinesource())
        .pipe(gulp.dest('./out'));
});
```

Optionally, you can provide [some options](https://github.com/popeindustries/inline-source#usage) through an options object:

```javascript
var gulp = require('gulp');
var inlinesource = require('gulp-inline-source');

gulp.task('inlinesource', function () {
    var options = {
        compress: false
    };

    return gulp.src('./src/*.html')
        .pipe(inlinesource(options))
        .pipe(gulp.dest('./out'));
});
```
