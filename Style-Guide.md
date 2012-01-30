# Style Guide
## General
* Indentation - 2 spaces
* Line Length - 80 characters

## Classes
The standard way of creating classes in pdf.js is the following. Please note that by class we mean an object that is class-like.
<pre>
var Name = (function NameClosure() {
  function Name(name) {
    this.name = name;
  }

  Name.prototype = {
  };
  ...

  return Name;
})();
</pre>