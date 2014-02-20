*This repository is a mirror of the [component](http://component.io) module [gamtiq/extend](http://github.com/gamtiq/extend). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/gamtiq-extend`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
# extend

Make one class (constructor function) inherited from another.

Based on [extend](http://yuilibrary.com/yui/docs/api/classes/YUI.html#method_extend) method from [YUI library](http://yuilibrary.com).

[![Build Status](https://travis-ci.org/gamtiq/extend.png)](https://travis-ci.org/gamtiq/extend)
[![Built with Grunt](https://cdn.gruntjs.com/builtwith.png)](http://gruntjs.com/)

## Installation

### Component

    component install gamtiq/extend

### Jam

    jam install extend

### Bower

    bower install extend

### AMD, Node, script tag

Use `dist/extend.js` or `dist/extend.min.js` (minified version).

## Usage

### Component

```js
var extend = require("extend");
...
```

### Node

```js
var extend = require("./path/to/dist/extend.js");
...
```

### Jam

```js
require(["extend"], function(extend) {
    ...
});
```

### AMD

```js
define(["path/to/dist/extend.js"], function(extend) {
    ...
});
```

### Bower, script tag

```html
<!-- Use bower_components/extend/dist/extend.js if the library was installed via Bower -->
<script type="text/javascript" src="path/to/dist/extend.js"></script>
<script type="text/javascript">
    // extend is available via extend field of window object
    ...
</script>
```

## Example

```js
var SuperClass = function(a, b) {
    ...
};
SuperClass.prototype.method1 = function(c, d, e) {
    ...
};
...
var SubClass = function(a, b) {
    ...
    SubClass.superconstructor.call(this, a, b);
    // or
    // SubClass.superconstructor.apply(this, arguments);
    ...
};
extend(SubClass, SuperClass);
...
SubClass.prototype.method1 = function(c, d, e) {
    ...
    SubClass.superclass.method1.call(this, c, d, e);
    // or
    // SubClass.superclass.method1.apply(this, arguments);
    ...
};
...
if (extend.isSubclass(SubClass, SuperClass)) {
    ...
}
```

See `test/extend.js` for additional examples.

## API

### extend(SubClass: Function, ParentClass: Function): Function

Replace value of `prototype` field of `SubClass` by another object that inherits from `prototype` of `ParentClass`.

Returns `SubClass`.

### extend.isSubclass(SubClass: Function, ParentClass: Function): Boolean

Test whether `SubClass` is inherited from `ParentClass`.

## Licence

MIT
