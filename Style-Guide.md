# Style Guide
## General
* Indentation - 2 spaces
* Line Length - 80 characters

## Naming
* variables and functions - lowerCamelCase
* constructor like functions - UpperCamelCase
* constants - ALL_UPPER_CASE_WITH_UNDERSCORES

## Braces
* No braces for single line control statements

```javascript
if (someVar)
  return true;
```
* Opening brace on the same line

```javascript
if (someVar) {
  someVar += 2;
  return someVar;
}
```

## White Space
* Space after control statements (if, else, while, for, ...)

```javascript
if (someVar)
```

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