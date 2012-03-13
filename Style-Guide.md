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
```
if (someVar)
  return true;
```
* Opening brace on the same line
```
if (someVar) {
  someVar += 2;
  return someVar;
}
```

## White Space
* Space after control statements (if, else, while, for, ...)
```
if (somevar)
```

## Classes
The standard way of creating classes in pdf.js is the following. Please note that by class we mean an object that is class-like.
```
var Name = (function NameClosure() {
  function Name(name) {
    this.name = name;
  }

  Name.prototype = {
    ...
  };

  return Name;
})();
```