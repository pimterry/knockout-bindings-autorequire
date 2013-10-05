# knockout-bindings-autorequire [![Build Status](https://travis-ci.org/pimterry/knockout-bindings-autorequire.png)](https://travis-ci.org/pimterry/knockout-bindings-autorequire) [![Dependency status](https://david-dm.org/pimterry/knockout-bindings-autorequire/dev-status.png)](https://david-dm.org/pimterry/knockout-bindings-autorequire#info=devDependencies&view=table)

Small simple Knockout plugin to let you tie dependency management of your knockout binding handlers to where they're actually used: the bindings themselves, by automatically finding the undefined bindings you're using and hooking into RequireJS (or any other AMD loader) to load them up.

Knockout-bindings-autorequire means you don't have to manually depend on and carefully load your knockout binding handlers yourself; just wrap your knockout binding application through this plugin's API, and every extra binding handler you're using will be automatically detected, and loaded and setup ready automatically.

**knockout-bindings-autorequire is still in a pre-release state, and the below is primarily an outline of the plans, not current functionality**

## Benefits

* Stop JavaScript viewmodels being tied to the specific bindings used in the HTML
* Automatically stop loading binding handlers as soon as you stop using them
* Never have to make JS changes just because the HTML is hooked up slightly differently

## Downloading loglevel

knockout-bindings-autorequire  is also available via [Bower](https://github.com/bower/bower) (`bower install knockout-bindings-autorequire `) or [JamJS](http://jamjs.org/packages/#/details/knockout-bindings-autorequire ) (`jam install knockout-bindings-autorequire `)

Alternatively if you just want to grab the file yourself, you can download either the current stable [production version][min] or the [development version][max] directly.

Finally, if you want to tweak knockout-bindings-autorequire  to your own needs or you immediately need the cutting-edge version, clone this repo and see [Developing & Contributing](#developing--contributing) below for build instructions.

[min]: https://raw.github.com/pimterry/knockout-bindings-autorequire/master/dist/knockout-bindings-autorequire.min.js
[max]: https://raw.github.com/pimterry/knockout-bindings-autorequire/master/dist/knockout-bindings-autorequire.js

## How to use it

Knockout-bindings-autorequire requires you to be using an AMD module loader, and using knockout as an AMD module. To use it with default options only, change your current code that looks like this:

```javascript
define(["knockout"], function (ko) {
  ko.applyBindings();
});
```

to this:

```javascript
define(["knockout", "knockout-bindings-autorequire!"], function (ko) {
  ko.applyBindings();
});
```

Alternatively, knockout-bindings-autorequire can be used as directly without even touching knockout, with:

```javascript
define(["knockout-bindings-autorequire"], function(koAutorequired) {
  koAutorequired.applyBindings(); // same API as ko.applyBindings(), but autorequires first
});
```

Finally, knockout-bindings-autorequire can be used as directly, with your own management of the binding process, by using:

```javascript
define(["knockout", "knockout-bindings-autorequire"], function (ko, autorequireBindings) {
  autorequireBindings(function () {
    ko.applyBindings();
  });
});
```

## Developing & Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality.

Builds can be run with grunt: run `grunt dist` to build a distributable version of the project (in /dist), or `grunt test` to just run the tests and linting. During development you can run `grunt watch` and it will monitor source files, and rerun the tests and linting as appropriate when they're changed.

_Also, please don't manually edit files in the "dist" subdirectory as they are generated via Grunt. You'll find source code in the "lib" subdirectory!_

#### Release process

To do a release of knockout-bindings-autorequire:

* Update the version number in package.json and bower.json
* Run `grunt dist` to build a distributable version in dist/
* Update the release history in this file (below)
* Commit the built code, tagging it with the version number and a brief message about the release
* Push to Github
* Run `jam publish` to publish to JamJS

## Release History

No releases yet: watch this space

## License
Copyright (c) 2013 Tim Perry  
Licensed under the MIT license.
