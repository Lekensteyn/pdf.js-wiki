This page outlines the style conventions that PDF.js follows to maintain a consistent codebase. We ask each contributor that creates a pull request to adhere to these conventions. Some of these conventions will also be checked automatically by a linting tool after each push to a branch of a pull request.

## General
* Indentation: 2 spaces
* Line length: 80 characters
* Required license in header: see https://github.com/mozilla/pdf.js/blob/master/src/license_header.js

## Naming
* Variables and functions: lowerCamelCase
* Constructor-like functions: UpperCamelCase
* Constants: ALL_UPPER_CASE_WITH_UNDERSCORES

## Braces
Always use braces and put them on same line, even for single line control statements:

```javascript
if (someVar) {
  return true;
} else {
  return null;
}
```

## White space
Keep one space after control statements (if, else, while, for, et cetera):

```javascript
if (someVar) {
```

## Equalities
Use only strict equalities (`===`) and inequalities (`!==`):

```javascript
if (someVar === conditionA) {
  return true;
} else if (someVar !== conditionB) {
  return false;
}
```

## Variables
Variables must be defined only once within a function scope, preferably at the top of the function.

## Classes
The standard way of creating classes in PDF.js is the following. Please note that by class we mean an object that is class-like. Also, note the naming of all anonymous functions.

```javascript
var ClassName = (function ClassNameClosure() {
  function ClassName(...) {
    ...
  }

  ClassName.prototype = {
    functionName: function ClassName_functionName(...) {
      ...
    },

    aLongFunctionName: function ClassName_aLongFunctionName(arg1,
                                                            arg2,
                                                            ...) {
      ...
    },

    aVeryLongFunctionName: 
        function ClassName_aVeryLongFunctionName(...) {
      ...
    }
  };

  return ClassName;
})();
```