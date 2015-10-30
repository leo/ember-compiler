# Huh?

Before Ember 1.10, developers who wanted to compile their templates on the server-side, had to use a package called "ember-template-compiler". When the new release came out, the guys behind Ember thankfully decided to create a single file for both the compilation on the client- and on the server-side.

This lead to a file called `ember-template-compiler.js` within Ember's bower package. That's the file that can be used for the compilation on the server and on the client.

> So why don't we just use the one from the bower package for the compilation on the server-side?

## Why [bower][1] if we have [npm][2]?

Many developer will now answer something like "Because npm sucks for front-end packaging stuff and bower does a better job at this", but I'd like to say "No!" right here.

Especially after [v3.0.0][3], npm introduced drastic changes to the way how packages are managed. Now everything is just flat and very easy to access when loading it for the front-end. And if you ask me, they will definitely go further into this direction!

So I decided to do the first step and use npm for my front-end stuff, too.

## Usage

1. Install the package: `npm install ember-compiler`
2. Start compiling your templates:

```js
var fs = require( 'fs' ),
    compiler = require( 'ember-compiler' ),
    input = fs.readFileSync( 'path/to/template.hbs', { encoding: 'utf8' } ),
    template = compiler.precompile( input, false ),
    output = 'export default Ember.HTMLBars.template(' + template + ');';

fs.writeFileSync( 'path/to/output.js', output, { encoding: 'utf8' } );
```

<br>
---

This package will always contain the latest code from `http://builds.emberjs.com/release/ember-template-compiler.js`, so make sure to keep it updated in your app.

[1]: http://bower.io
[2]: https://www.npmjs.com
[3]: https://github.com/npm/npm/releases/tag/v3.0.0
