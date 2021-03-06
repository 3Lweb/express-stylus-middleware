# Express Stylus middleware
Stylus-to-CSS conversion middleware for Express to make simple magic on the fly.  
It's a Stylus-version of [Express-less](https://github.com/toogle/express-less) middleware

## Installation
```bash
npm i express-stylus-middleware -S
```

## Usage
```js
const express = require("express");
const expressStylus = require("express-stylus-middleware");  
const app = express();  

app.use("/css", expressStylus(__dirname + "/stylus-css"));
```

Also you can use cache:
```js
app.use("/css", expressStylus(__dirname + "/stylus-css"), { cache: true });
```
And make compressed css:
```js
app.use("/css", expressStylus(__dirname + "/stylus-css", { compress: true }));
```
Additionally, you can use some Stylus's in-build options (in theory, not tested):

```
`force`     Always re-compile
`compile`   Custom compile function, accepting the arguments
              `(str, path)`.
`firebug`   Emits debug infos in the generated css that can
              be used by the FireStylus Firebug plugin
`linenos`   Emits comments in the generated css indicating 
              the corresponding stylus line
`sourcemap` Generates a sourcemap in sourcemaps v3 format
```

### Autoprefixer
Even if you don't use task runners or bundlers, you can turn on [PostCSS/Autoprefixer](https://github.com/postcss/autoprefixer):
```js
app.use("/css", expressStylus(__dirname + "/stylus-css", {
    autoprefixer: true
}));
```
By default browsers option is set to `last 2 versions`. You can modify it:
```js
app.use("/css", expressStylus(__dirname + "/stylus-css", {
    autoprefixer: { browsers: ['Firefox > 20']}
}));
```
You can set all [Autoprefixer options](https://github.com/postcss/autoprefixer#options) in the same way.

### Usage with express.static
You have to use `express-stylus-middleware` before `express.static`
```js
app.use('/css', expressStylus(__dirname + '/stylus-css'));
app.use(express.static('public'));
```

## Testing
```bash
npm test
```
    
## Licence
MIT
