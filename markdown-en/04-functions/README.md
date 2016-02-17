# Functions

```javascript
function sum(a, b) {
  var c = a + b;
  return c;
}
```

**functions** allow us to group several lines of code under a single name.
This way, we can reuse this code, by invoking the name of the function.

They consist of the following parts:

- The `function` sentence
- The function _name_ (_sum_)
- _Parameters_ (arguments) expected by the function (_a_ and _b_)
A function can accept zero or more arguments separated by commas
- A code block, also called _body of the function_
- _`return`_ sentence
A function always returns a value.
When it does not return explicitly a value, implicitly returns the value `undefined`

A function can _only return one value._
When it needs to return more than a value, it can return an array or an object with those values

To call a function we only need to write its name followed by some parameters (or none) between parenthesis

```javascript
>>> var result = sum(1, 2);
>>> result;
3
```

<sub>[https://developer.mozilla.org/en/JavaScript/Reference/Functions_and_function_scope](https://developer.mozilla.org/en/JavaScript/Reference/Functions_and_function_scope)</sub>  
<sub>[https://developer.mozilla.org/es/Referencia_de_JavaScript_1.5/Objetos_globales/Function](https://developer.mozilla.org/es/Referencia_de_JavaScript_1.5/Objetos_globales/Function)</sub>  
<sub>[https://bonsaiden.github.io/JavaScript-Garden/#function](https://bonsaiden.github.io/JavaScript-Garden/#function)</sub>  

## Parameters

A function can be defined to not require parameters, but if they are required and they are not provided in the call of the function, Javascript will assign the value `undefined` to them

If the function receives more parameters than expected, it will simply ignore them

Inside every function we have available the object (pseudo-array) [`arguments`](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Obsolete_Pages/Gu%C3%ADa_JavaScript_1.5/Usando_el_objeto_arguments) that contains the arguments passed to the function

```javascript
function sumOnSteroids() {
  var i, res = 0;
  var number_of_params = arguments.length;
  for (i = 0; i < number_of_params; i++) {
    res += arguments[i];
  }
  return res;
}
```

## Pre-defined functions

There are some functions that are already defined inside the Javascript engine.
These pre-defined functions are (among others):

- `parseInt()`
- `parseFloat()`
- `isNaN()`
- `isFinite()`
- `encodeURI()`
- `decodeURI()`
- `encodeURIComponent()`
- `decodeURIComponent()`
- `eval()`

###[parseInt()](https://developer.mozilla.org/es/Referencia_de_JavaScript_1.5/Funciones_globales/parseInt)

`parseInt()` takes a value and tries to transform it into an integer
If the transformation fails it returns `NaN`.
`parseInt()` can take a second optional parameter that sets the numerical base of the number passed as first argument (decimal, hexadecimal, binary, etc…)

```javascript
>>> parseInt('123')
123
>>> parseInt('abc123')
NaN
>>> parseInt('1abc23')
1
>>> parseInt('123abc')
123
```

It is recommended to especify always the expected base (usually _10_) to [avoid interpretation issues](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt#Octal_interpretations_with_no_radix)

```javascript
>>> parseInt(" 0xF", 16);
15
>>> parseInt(" F", 16);
15
>>> parseInt("17", 8);
15
>>> parseInt(021, 8);
15
>>> parseInt("015", 10);
15
>>> parseInt(15.99, 10);
15
>>> parseInt("FXX123", 16);
15
>>> parseInt("1111", 2);
15
>>> parseInt("15*3", 10);
15
>>> parseInt("15e2", 10);
15
>>> parseInt("15px", 10);
15
>>> parseInt("12", 13);
15
```

###[parseFloat()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseFloat)

`parseFloat()` takes a value and tries to transform it into a float number (with decimals).

```javascript
>>> parseFloat('123')
123
>>> parseFloat('1.23')
1.23
>>> parseFloat('1.23abc.00')
1.23
>>> parseFloat('a.bc1.23')
NaN
```

###[isNan()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isNaN)

`isNan()` checks if the value passed as a parameter is a valid number (returns `true` in case is not)

```javascript
>>> isNaN(NaN)
true
>>> isNaN(123)
false
>>> isNaN(1.23)
false
>>> isNaN(parseInt('abc123'))
true
```

###[isFinite()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isFinite)

`isFinite()` checks if the value passed as a parameter is not `Infinity` or `NaN`

```javascript
>>> isFinite(Infinity)
false
>>> isFinite(-Infinity)
false
>>> isFinite(12)
true
>>> isFinite(1e308)
true
>>> isFinite(1e309)
false
```

###[encodeURI()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURI)

`encodeURI()` allows us to 'escape' (encode) a URL replacing some characters by its related escape sequence (UTF-­8 ).
_encodeURI()_ returns an usable URL (only encodes some characters)

```javascript
>>> var url = 'http://www.packtpub.com/scr ipt.php?q=this and that';
>>> encodeURI(url);
http://www.packtpub.com/scr%20ipt.php?q=this%20and%20that
```

###[decodeURI()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/decodeURI)

`decodeURI()` Allows us to 'decode' a string encoded by `encodeURI()`

###[encodeURIComponent()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent) y [decodeURIComponent()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/decodeURIComponent)

`encodeURIComponent()` (and `decodeURIComponent()`) works like
`encodeURI()` but this function encodes (or decodes) ALL transformable characters

```javascript
>>> encodeURIComponent(url);
"http%3A%2F%2Fwww.packtpub.com%2Fscr%20ipt.php%3Fq%3Dthis%20and%20that"
```

###[eval()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/eval)

`eval()` takes a text and executes it as Javascript code

`eval()` should not be used due the following reasons:

- _Perfomance_: It is much more slower evaluating "live" code than having it directly in the script
- _Security_: Be aware that every element passed as a parameter could be a security hole in your application

```javascript
>>> eval('var ii = 2;')
>>> ii
2
```

<sub>[http://bonsaiden.github.com/JavaScript-­‐Garden/#core.eval](http://bonsaiden.github.com/JavaScript-­‐Garden/#core.eval)</sub>

###alert()

`alert()` displays a window on the browser with a string of text 
`alert()` is not part of the JS core but is available in all browsers

WARNING! `alert()` blocks (stops) the code execution until the message is acknowledged by the user


<br/>

## Function Scope

In Javascript variables are defined in the function scope (and not in the block scope as it happens in other programming languages)

- **Global variables** are those defined outside any function
- **Local variables** are those defined inside a function


<br/>

## Callback Functions

_Functions in Javascript are data (values)_, which means that they can be assigned to variables in the same way we do with other values (and manage them as variables)

```javascript
function f(){ return 1; }
var f = function(){ return 1; }
```

Functions are data, but a special type of data (`typeof ‘function’`) because:

- They contain code
- We can execute them

```javascript
>>> var sum = function(a, b) { return a + b; }
>>> var add = sum;
>>> delete sum
true
>>> typeof sum;
"undefined"
>>> typeof add;
"function"
>>> add(1, 2);
3
```

**Anonymous functions** are those that does not have a name and can be used to:

- Pass that function as an argument of a function
- Define a function and execute it inmediately

```javascript
>>> function(a){ return a; }
```

When we pass a function A as an argument of another function B and B executes A, we say that A is a **[callback function](http://stackoverflow.com/questions/483073/getting-­‐a-­‐better-­‐understanding-­‐of-­‐callback-­‐functions-­‐in-­‐javascript)**

```javascript
>>> function invoke_and_add(a, b){ return a() + b(); }
>>> function one() { return 1; }
>>> function two() { return 2; }
>>> invoke_and_add(one, two);
3
>>> invoke_and_add(one, function(){return 7;})
8
```

<br/>

## Closures

If we define a function `n()` inside of another function `f()` , `n()` will have access to all the variables in its scope and its father's scope. This is what is called **scope chain**

```javascript
var a = 1;
function f(){
  var b = 1;
  function n() {
    var c = 3;
  }
}
```

<sub>[http://stackoverflow.com/questions/1484143/scope-­‐chain-­‐in-­‐javascript](http://stackoverflow.com/questions/1484143/scope-­‐chain-­‐in-­‐javascript)</sub>
<sub>[http://www.digital-­‐web.com/articles/scope_in_javascript/](http://www.digital-­‐web.com/articles/scope_in_javascript/)</sub>  
<sub>[http://odetocode.com/Blogs/scott/archive/2007/07/10/closure-­‐on-­‐javascript-­‐closures.aspx](http://odetocode.com/Blogs/scott/archive/2007/07/10/closure-­‐on-­‐javascript-­‐closures.aspx)</sub>  
<sub>[http://www.smashingmagazine.com/2009/08/01/what-­‐you-­‐need-­‐to-­‐know-­‐about-­‐javascript-­‐scope/](http://www.smashingmagazine.com/2009/08/01/what-­‐you-­‐need-­‐to-­‐know-­‐about-­‐javascript-­‐scope/)</sub>  

Functions have what is called a **lexical scope** which means that they create their scope (which variables they have access to) when they are defined, not when they are executed

```javascript
>>> function f1(){ var a = 1; return f2(); }
>>> function f2(){ return a; }
>>> f1();
a is not defined
>>> var a = 5;
>>> f1();
5
>>> a = 55;
>>> f1();
55
>>> delete a;
true
>>> f1();
a is not defined
```

```javascript
var a = 123;
function f() {
  alert(a);
  var a = 1;
  alert(a);
}
f();
```

<sub>[https://developer.mozilla.org/en/JavaScript/Guide/Closures](https://developer.mozilla.org/en/JavaScript/Guide/Closures)</sub>  
<sub>[http://stackoverflow.com/questions/1047454/what-­‐is-­‐lexical-­‐scope](http://stackoverflow.com/questions/1047454/what-­‐is-­‐lexical-­‐scope)</sub>  
<sub>[http://ayende.com/Blog/archive/2007/12/13/Javascript-­‐lexical-­‐scopes-­‐and-­‐what-­‐your-­‐momma-­‐thought-­‐you-­‐about.aspx](http://ayende.com/Blog/archive/2007/12/13/Javascript-­‐lexical-­‐scopes-­‐and-­‐what-­‐your-­‐momma-­‐thought-­‐you-­‐about.aspx)</sub>  

A **closure** is created when a function maintains a link with the scope of the father, even after the parent function has finished

```javascript
function f(){
  var b = "b";
  return function(){
    return b;
  }
}
>>> b
b is not defined
>>> var n = f();
>>> n();
"b"
```

```javascript
var n;
function f(){
  var b = "b";
  n = function(){
    return b;
  }
}
>>> f();
>>> n();
```

```javascript
function f(arg) {
  var n = function(){
    return arg;
  };
  arg++;
  return n;
};
>>> var m = f(123);
>>> m();
```

<sub>[http://mark-­‐story.com/posts/view/picking-­‐up-­‐javascript-­‐closures-­‐and-­‐lexical-­‐scoping](http://mark-­‐story.com/posts/view/picking-­‐up-­‐javascript-­‐closures-­‐and-­‐lexical-­‐scoping)</sub>  
<sub>[http://blog.morrisjohns.com/javascript_closures_for_dummies.html](http://blog.morrisjohns.com/javascript_closures_for_dummies.html)</sub>  
<sub>[http://stackoverflow.com/questions/111102/how-­‐do-­‐javascript-­‐closures-­‐work](http://stackoverflow.com/questions/111102/how-­‐do-­‐javascript-­‐closures-­‐work)</sub>  
<sub>[http://www.kryogenix.org/code/browser/secrets-­‐of-­‐javascript-­‐closures/](http://www.kryogenix.org/code/browser/secrets-­‐of-­‐javascript-­‐closures/)</sub>  
<sub>[http://www.hunlock.com/blogs/Closing_The_Book_On_Javascript_Closures](http://www.hunlock.com/blogs/Closing_The_Book_On_Javascript_Closures)</sub>
<sub>[http://jibbering.com/faq/notes/closures/](http://jibbering.com/faq/notes/closures/)</sub>  
<sub>[http://www.bennadel.com/blog/1482-­‐A-­‐Graphical-­‐Explanation-­‐Of-‐Javascript-­‐Closures-­‐In-­‐A-­‐jQuery-­‐Context.htm](http://www.bennadel.com/blog/1482-­‐A-­‐Graphical-­‐Explanation-­‐Of-‐Javascript-­‐Closures-­‐In-­‐A-­‐jQuery-­‐Context.htm)</sub>  
