<!--
---
title: DownloadButton Demos
colors: pink
fontPair: Fugaz One
ga: UA-7002862-5
source: https://github.com/notablemind/downloadbutton/raw/master/Readme.md
css: |
  .DownloadButton {
    font-size: 16px;
    font-family: sans-serif;
  }
styles:
  - https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.3.0/css/font-awesome.min.css
  - https://cdnjs.cloudflare.com/ajax/libs/materialize/0.95.0/css/materialize.min.css
scripts:
  - download-button.js
  - https://code.jquery.com/jquery-2.1.1.min.js
  - https://cdnjs.cloudflare.com/ajax/libs/materialize/0.95.0/js/materialize.min.js
links:
  home:
  demos: demo.html
  github: https://github.com/notablemind/downloadbutton

---
-->

<!-- @demobox hide -->
View this page rendered at [notablemind.github.io/downloadbutton](http://notablemind.github.io/downloadbutton)
<!-- @demobox /hide -->

DownloadButton is a simple component for letting the user **download a
javascript-generated file.** It was extracted from
[Notablemind](https://github.com/notablemind/notablemind).

The styling is due to [materializecss](http://materializecss.com/), and does
not come with the `DownloadButton` component. You are free to style the
component however you wish.

## Demo

```jsx
// @demobox
function makeFile() {
  // do some calculations
  return {
    mime: 'text/plain',
    filename: 'myexportedfile.txt',
    contents: 'all of the exports',
  }
}


<DownloadButton
  // these classes come from materializecss
  className='waves-effect waves-light btn' 
  genFile={makeFile}/>
```

For more demos, see [the demo page](demo.md).

## Node Start

```bash
npm install --save downloadbutton
```

```js
var DownloadButton = require('downloadbutton')

// use it somewhere!
```

If you're not using browserify, you'll need to use the precompiled version, as
the source is written using `jsx` and `es6` syntax.

```js
var DownloadButton = require('downloadbutton/es5')

// use it
```

## API

### Props
[view demo](https://notablemind.github.io/downloadbutton/demo.html)

When `async=true`, the behavior is differnet. See the next section. See a demo
on [the demo page](demo.md).

Name | Type | Description
--- | --- | ---
`fileData` | `fileData` | If passed in, genFile will be ignored, and this file will be served.
`genFile` | `fn () -> fileData` or `fn (done: fn(fileData))` | Synchronous functions can just return the `fileData` object. If the `async` prop is `true`, then `genFile` should accept a callback function.
`downloadTitle` | `string` or react element, or `fn (fileData) -> string / react element` | The text shown on the button. If a function, it will be passed the `fileData` in the case that it has been passed in as props. Default: `"Download"`

You must pass in either `fileData` or `genFile`.

### Props (async=true)
[view demo](https://notablemind.github.io/downloadbutton/demo.html#asynchronous-generation)

If `fileData` is passed in, the `async` prop is **ignored**, and the component
will use the synchronous behavior.

Name | Type | Description
--- | --- | ---
`async` | `bool` | Set to true if `genFile` is an async function. Default: false.
`generateTitle` | `string` or react element | The text shown initially. Default: `"Generate file"`
`loadingTitle` | `string` or react element | The text shown while the file is being generated. Default: `"Loading..."`
`downloadTitle` | `string` or react element, or `fn (fileData) -> string / react element` | The text shown on the button. If a function, it will be passed the generated `fileData`. Default: `"Download"`

### The `fileData` type

```json
{
  mime: str,
  filename: str,
  content: str
}
```





