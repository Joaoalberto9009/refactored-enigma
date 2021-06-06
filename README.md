Evernote Javascript style guide
======================

Based off of [AirBnB's style guide](https://github.com/airbnb/javascript).

*Keeping our JavaScript more consistent*

## Table of Contents

  1. [Strings](#strings)
  2. [Variables](#variables)
  3. [Semicolons](#semicolons)
  4. [Commas](#commas)
  5. [Declaring Strict Mode](#declaring-strict-mode)
  6. [Naming Conventions](#naming-conventions)
  7. [Conditional Expressions](#conditional-expressions)
  8. [Blocks](#blocks)
  9. [Tab Spacing](#tab-spacing)
  10. [Types](#types)
  11. [Objects](#objects)
  12. [Arrays](#arrays)
  13. [Properties](#properties)
  14. [Accessors](#accessors)
  15. [Tools](#tools)
  16. [License](#license)

## Strings

Use single quotes `''` for strings instead of double quotes `""`

  ```javascript
  // bad
  var name = "Eva Note";

  var fullName = "Eva " + this.lastName;

  // good
  var name = 'Eva Note';

  var fullName = 'Eva ' + this.lastName;
  ```

**[⬆ back to top](#table-of-contents)**


## Variables

Declarations for `var` as follows:

  ```javascript
  // bad
  var a = 1;
  var b = 2;
  var c = 'string';

  // good
  var a = 1,
   b = 2,
   c = 'string';
  ```
**[⬆ back to top](#table-of-contents)**


## Semicolons

Use semicolons `;`

  ```javascript
  // bad
  function() {
    return 'Evernote'
  }

  // good
  function() {
    return 'Evernote';
  }
  ```

**[⬆ back to top](#table-of-contents)**

## Commas

Don't use leading commas.

  ```javascript
  // bad
  var evernote
    , premium
    , business;

  // good
  var evernote,
      premium,
      business;

  // bad
  var product = {
      name: 'Evernote'
    , type: 'App'
    , category: 'Productivity'
  };

  // good
  var product = {
    name: 'Evernote',
    type: 'App',
    category: 'Productivity'
  };

  // good
  function() {
    return 'Evernote';
  }
  ```

**[⬆ back to top](#table-of-contents)**

## Naming conventions

  - Use descriptive naming. Avoid single letter names.

  ```javascript
  // bad
  function t() {
    // do something...
  }

  // good
  function test() {
    // do something...
  }
  ```

  - Use camelCase when naming objects, functions, and instances.

  ```javascript
  // bad
  var OBject = {};
  var heres_an_object = {};
  function c() {}
  var u = new user({
    name: 'Evernote';
  });

  // good
  var thisIsMyObject = {};
  function thisIsMyFunction() {}
  var user = new User({
    name: 'Evernote';
  });
  ```

**[⬆ back to top](#table-of-contents)**


## Declaring Strict Mode

Declare `'use strict'` in all your JavaScript files.


**[⬆ back to top](#table-of-contents)**

##Conditional Expressions

Use `===` and `!==`

```javascript
  // bad
  var name = 'Eva Note';
  if(name == 'Eva Note'){}

  if(name != 'Eva Note'){}

  // good
  var name = 'Eva Note';
  if(name === 'Eva Note'){}

  if(name !== 'Eva Note'){}
  ```
**[⬆ back to top](#table-of-contents)**


##Blocks

Use braces when there are multi-line blocks.

```javascript
  // bad
  if (name)
  return false;

  // good
  if (name) return false;

  // bad
  if (name){return false};

  // good
  if (name){
    return false;
  }
  ```
**[⬆ back to top](#table-of-contents)**

##Tab Spacing

Use two spaces for tabs

```javascript
  // bad
  function() {
  ∙∙∙∙return true;
  }

  // good
  function() {
  ∙∙return true;
  }
  ```
**[⬆ back to top](#table-of-contents)**

## Types

  - **Primitives**: When you access a primitive type you work directly on its value

    + `string`
    + `number`
    + `boolean`
    + `null`
    + `undefined`

    ```javascript
    var foo = 1,
        bar = foo;

    bar = 9;

    console.log(foo, bar); // => 1, 9
    ```
  - **Complex**: When you access a complex type you work on a reference to its value

    + `object`
    + `array`
    + `function`

    ```javascript
    var foo = [1, 2],
        bar = foo;

    bar[0] = 9;

    console.log(foo[0], bar[0]); // => 9, 9
    ```

**[⬆ back to top](#table-of-contents)**

## Objects

  - Use the literal syntax for object creation.

    ```javascript
    // bad
    var item = new Object();

    // good
    var item = {};
    ```

  - Don't use [reserved words](http://es5.github.io/#x7.6.1) as keys. It won't work in IE8.

    ```javascript
    // bad
    var superman = {
      default: { clark: 'kent' },
      private: true
    };

    // good
    var superman = {
      defaults: { clark: 'kent' },
      hidden: true
    };
    ```

  - Use readable synonyms in place of reserved words.

    ```javascript
    // bad
    var superman = {
      class: 'alien'
    };

    // bad
    var superman = {
      klass: 'alien'
    };

    // good
    var superman = {
      type: 'alien'
    };
    ```

**[⬆ back to top](#table-of-contents)**

## Arrays

  - Use the literal syntax for array creation

    ```javascript
    // bad
    var items = new Array();

    // good
    var items = [];
    ```

  - If you don't know array length use Array#push.

    ```javascript
    var someStack = [];


    // bad
    someStack[someStack.length] = 'abracadabra';

    // good
    someStack.push('abracadabra');
    ```

  - When you need to copy an array use Array#slice. [jsPerf](http://jsperf.com/converting-arguments-to-an-array/7)

    ```javascript
    var len = items.length,
        itemsCopy = [],
        i;

    // bad
    for (i = 0; i < len; i++) {
      itemsCopy[i] = items[i];
    }

    // good
    itemsCopy = items.slice();
    ```

  - To convert an array-like object to an array, use Array#slice.

    ```javascript
    function trigger() {
      var args = Array.prototype.slice.call(arguments);
      ...
    }
    ```

**[⬆ back to top](#table-of-contents)**


## Properties

  - Use dot notation when accessing properties.

    ```javascript
    var evernote = {
      elephant: true,
      remember: true
    };

    // bad
    var isElephant = evernote['elephant'];

    // good
    var isElephant = evernote.elephant;
    ```

  - Use subscript notation `[]` when accessing properties with a variable.

    ```javascript
    var evernote = {
      elephant: true,
      remember: true
    };

    function getProp(prop) {
      return evernote[prop];
    }

    var isElephant = getProp('elephant');
    ```

**[⬆ back to top](#table-of-contents)**

## Accessors

  - Accessor functions for properties are not required
  - If you do make accessor functions use getVal() and setVal('hello')

    ```javascript
    // bad
    elephant.age();

    // good
    elephant.getAge();

    // bad
    elephant.age(25);

    // good
    elephant.setAge(25);
    ```

  - If the property is a boolean, use isVal() or hasVal()

    ```javascript
    // bad
    if (!elephant.age()) {
      return false;
    }

    // good
    if (!elephant.hasAge()) {
      return false;
    }
    ```

**[⬆ back to top](#table-of-contents)**

## Tools

#### Sublime
  - [JSHint](https://github.com/uipoet/sublime-jshint)
  - [jsfmt](https://github.com/paulirish/sublime-jsfmt)

#### Grunt
  - [JSHint](https://github.com/gruntjs/grunt-contrib-jshint)

#### Gulp
  - [JSHint](https://github.com/spenceralger/gulp-jshint)

**[⬆ back to top](#table-of-contents)**

## License

(The MIT License)

Copyright (c) 2014 Airbnb

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[⬆ back to top](#table-of-contents)**

# };
