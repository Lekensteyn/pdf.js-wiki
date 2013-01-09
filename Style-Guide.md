# Style Guide
## General
* Indentation - 2 spaces
* Line Length - 80 characters
* [Required License in File Header](https://github.com/mozilla/pdf.js/wiki/License-Headers)

## Naming
* variables and functions - lowerCamelCase
* constructor like functions - UpperCamelCase
* constants - ALL_UPPER_CASE_WITH_UNDERSCORES

## Braces
* Always use braces and put them on same line even for single line control statements

```javascript
if (someVar) {
  return true;
} else {
  return null;
}
```
_Note: This wasn't always followed, but any new code should do this._

## White Space
* Space after control statements (if, else, while, for, ...)

```javascript
if (someVar) {
```

## Equalities
* Use only strict equalities (and inequalities) in control statements, e.g.

```javascript
if (someVar === conditionA) {
  return true;
} else if (someVar !== conditionB) {
  return false;
}
```

_Note: This wasn't always followed, but any new code should do this._

## Classes
The standard way of creating classes in pdf.js is the following. Please note that by class we mean an object that is class-like. Also, note the naming of all anonymous functions.

```javascript
var ClassName = (function ClassNameClosure() {
  function ClassName(...) {
    ...
  }

  ClassName.prototype = {
    functionName: function ClassName_functionName(...) {
      ...
    }
  };

  return ClassName;
})();
```