## RemCSS

A much leaner and quicker npm package for trimming unused CSS from CSS files based on the selectors matched in provided HTML files


### Getting Started


#### Browser-based
Head over to [https://rem-css.infinityfreeapp.com](https://rem-css.infinityfreeapp.com) for a more comprehensive, simple, UI-based trimming and downloading of used styles for your provided website URL.

___

#### Via the command line
+ Clone the repository
```
git clone https://github.com/ogbotemi-2000/RemCSS.git
```

+ Or install the package locally via npm

```
npm install remcss
```

_Both options above are quick and direct - the package has zero dependencies, no `npm install` required_


### Usage

The browser-based version is direct and progressive with short texts when necessary to guide its usage.


The section below comprises guides for using the package programatically

#### As a module

```js
const rem_css = require('remcss');

rem_css({
  html: /* array of html filenames or a filename */,
  css:  /* array of css filenames or a filename */
  out: /* output directory for the trimmed css files */

})

/* defaults to {html:'./', css:'css', out:'dist'}.
 * 'dist' is created if it does not exist
 */
rem_css()

```
___

#### Via invocation from the command-line

+ ##### Via `npm run <script> <arguments>`

Include the code block below in your `package.json` file for it to work
```js
...
  "scripts": {
    ...
    "remcss": "node ./node_modules/remcss/index"
    ...
  }
...
```

It is invoked as 
```js
npm run remcss -- -html <html file names or folder path> -css <similar but for css> -out <output folder>
```
An example - `npm run remcss -- -h 'index.html, sitemap.html' -c public/css -o dist`, the double dashes are required for proper behaviour


+ ##### Via `node path/to/remcss/index`
```js
node path/to/remcss/index -h index.html -c 'tailwind.css, all.css' -o output-folder
```


The arguments can also be provided in the long version
```js
node path/to/remcss/index.js --html 'index.html, 404.html' --css 'tailwind.css, all.css' -output output-folder
```

> The arguments above can be anything, what matters is that their initial letters - 'h', 'c', 'o' as speciified in the `index.js` file remain in the same position:
```js

... argv(['-h', '-c', '-o'], ['./', 'css', 'dist']) ...
```

### Caveats

1. Regular expressions, used by the code, that are of this form `[^, }]+\}` appear to perform less thoroughly in Node.js than in the browser, use the browser-based version of this code for a comprehensive removal of unused styles

2. A performance drop may be detected by the package for large CSS files of over 1MB, follow the prompts it shows to use an alternative workaround


### License

Distributed under the EPUL License. See 'LICENSE.txt' for more information

Copyright © 2024 [Ogbotemi Akin Ogungbamila](https://github.com/ogbotemi-2000)


### Discuss

[Discussions are welcome!](https://github.com/ogbotemi-2000/RemCSS/discussions/)

### Contact

Ogbotemi Akin Ogungbamila

+ Twitter: [@ogbotemi_o](https://twitter.com/ogbotemi_o)

### Acknowledgements

+ [W3C CSS Specification for selectors](https://www.w3.org/TR/selectors-3/#sequence): For the documents from which the algorithm used in validating used CSS selectors was created
