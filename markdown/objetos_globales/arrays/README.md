#[Array](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array)

- Para crear arrays podemos usar:
    - La notacion literal :  `var a = []`
    - La funcion constructora Array():  `var o = new Array();`

- Podemos pasarle parametros al constructor `Array()`
    - Varios parametros: Seran asignados como elementos al array
    - Un numero: Se considerará el tamaño del array

```javascript
>>> var a = new Array(1,2,3,'four');
>>> a;
[1, 2, 3, "four"]

>>> var a2 = new Array(5);
>>> a2;
[undefined, undefined, undefined, undefined, undefined]
```

- Como los arrays son objetos tenemos disponibles los metodos y propiedades del padre `Object()`

```javascript
>>> typeof a;
"object"

>>> a.toString();
"1,2,3,four"
>>> a.valueOf()
[1, 2, 3, "four"]
>>> a.constructor
Array()
```
- Los arrays disponen de la propiedad [`length`](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/length)  

    - Nos devuelve el tamaño del array (numero de elementos)
    - Podemos  modificarlo y cambiar el tamaño del array

```javascript
>>> a[0] = 1; 
>>> a.prop = 2; 

>>> a.length
1
>>> a.length = 5
5
>>> a
[1, undefined, undefined, undefined, undefined]

>>> a.length = 2;
2
>>> a
[1, undefined]
```
  
  
Los arrays disponen de unos cuantos metodos interesantes:

- `push()`
- `pop()`
- `sort()`
- `join()`
- `slice()`
- `splice()`

```javascript
>>> var a = [3, 5, 1, 7, 'test'];

>>> a.push('new') 
6
>>> a 
[3, 5, 1, 7, "test", "new"]

>>> a.pop() 
"new"
>>> a 
[3, 5, 1, 7, "test"]

>>> var b = a.sort();
>>> b
[1, 3, 5, 7, "test"]
>>> a
[1, 3, 5, 7, "test"]

>>> a.join(' is not ');
"1 is not 3 is not 5 is not 7 is not test"

>>> b = a.slice(1, 3);
[3, 5]
>>> a
[1, 3, 5, 7, "test"]

>>> b = a.splice(1, 2, 100, 101, 102);
[3, 5]
>>> a
[1, 100, 101, 102, 7, "test"]
```

## Métodos de Array

###[concat()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

`concat()` crea _otro array_ a partir de uno ya existente añadiendole los elementos que se le pasen 

```javascript
>>> var items = [1,2]
>>> items.concat(3,4,5)
[1, 2, 3, 4, 5]
>>> items.concat(3,4,5,'string',undefined)
[1, 2, 3, 4, 5, "string", undefined]
>>> items.concat([3,4,5],[6,7],[8,9])
[1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> items.concat([3,4,5],[6,7,[8,9,10]])
[1, 2, 3, 4, 5, 6, 7, [8,9,10]]
```

[concat w/ forEach example](https://jsbin.com/kicawe/1/edit?js,console)

###[join()](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/join)

`join()` devuelve una cadena (string) con los valores de los elementos del array 

```javascript
>>> var a = ['Wind', 'Rain', 'Fire'];
>>> a.join();
"Wind,Rain,Fire"
>>> a.join(" - ");
"Wind - Rain - Fire"
>>> typeof ( a.join(" - ") )
"string"
```

###[indexOf()](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/indexOf)

`indexOf()` devuelve el primer indice donde se encuentra un elemento en el array o -1 si no lo encuentra

```javascript
>>> var a = ['Wind', 'Rain', 'Fire'];
>>> a.indexOf('Rain');
1
>>> a.indexOf('Earth');
-1
>>> a.indexOf('rain');
-1
>>> a.indexOf('Rain',2);
1
```

###[push()](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/push)

`push()` inserta elementos al final del array  
`a.push('new')` es lo mismo que `a[a.length] = 'new'`  
`push()` devuelve el tamaño del array modificado  

```javascript
>>> var sports = ['soccer', 'baseball'];
>>> sports
["soccer", "baseball"]
>>> sports.length
2
>>> sports.push('football', 'swimming');
4
>>> sports
["soccer", "baseball", "football", "swimming"]
```

###[pop()](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/pop)

`pop()` elimina el ultimo elemento   
`a.pop()` es lo mismo que `a.length--`;  
`pop()` devuelve el elemento eliminado  

```javascript
>>> var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
>>> myFish
["angel", "clown", "mandarin", "sturgeon"]
>>> myFish.pop();
"sturgeon"
>>> myFish
["angel", "clown", "mandarin"]
```

###[sort()](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/sort)

ordena el array y devuelve el array modificado  
si no se le pasa función como parametro ordena por orden ASCII  
si se le pasa función como parametro
- `compare(a, b)` → -1  → a,b
- `compare(a, b)` → 1   → b,a (switch)
- `compare(a, b)` → 0   → a,b (do nothing)

```javascript
>>> var fruit = ['apples', 'bananas', 'Cherries'];
>>> fruit
["apples", "bananas", "Cherries"]
>>> fruit.sort();
["Cherries", "apples", "bananas"]

>>> var scores = [1, 2, 10, 21];
>>> scores
[1, 2, 10, 21]
>>> scores.sort()
[1, 10, 2, 21]
```

```javascript
>>> var numbers = [4, 2, 42, 36, 5, 1, 12, 3];
>>> numbers
[4, 2, 42, 36, 5, 1, 12, 3]
>>> numbers.sort()
[1, 12, 2, 3, 36, 4, 42, 5]
>>> numbers.sort( function(a, b) { return a - b; } );
[1, 2, 3, 4, 5, 12, 36, 42]
```

```javascript
function compare(a, b) {
  if (a is less than b by some ordering criterion) {
    return -1; // a comes first
  }
  if (a is greater than b by the ordering criterion) {
    return 1; // b comes first
  }
  // a must be equal to b
  return 0; // no changes
}
```

###[slice()](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/slice)

`slice()` devuelve un trozo del array  sin modficar el original 

```javascript
>>> var fruits = ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango'];
>>> var citrus = fruits.slice(1, 3);
>>> fruits
["Banana", "Orange", "Lemon", "Apple", "Mango"]
>>> citrus
["Orange", "Lemon"]
>>> fruits.slice(1)
["Orange", "Lemon", "Apple", "Mango"]
>>> fruits.slice(1).slice(1)
["Lemon", "Apple", "Mango"]
>>> fruits.slice(-1)
["Mango"]
>>> fruits.slice(-2)
["Apple", "Mango"]
>>> fruits.slice(1,-1)
["Orange", "Lemon", "Apple"]
```

###[splice()](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/splice)

`splice()` quita un trozo del array, lo devuelve  y opcionalmente rellena el hueco con nuevos elementos 

```javascript
>>> var myFish = ['angel', 'clown', 'mandarin', 'surgeon'];

>>> myFish
["angel", "clown", "mandarin", "surgeon"]
>>> var removed = myFish.splice(2, 1);

>>> myFish
["angel", "clown", "surgeon"]
>>> removed
["mandarin"]

>>> var removed = myFish.splice(2, 0, 'drum');
>>> myFish
["angel", "clown", "drum", "surgeon"]
>>> removed
[]
```

## Higher Order Functions

<sub>[Functional Programming in JavaScript | YouTube Videos](https://www.youtube.com/watch?v=BMUiFMZr7vk&list=PL0zVEGEvSaeEd9hlmCXrk5yUyqUag-n84)</sub>  
<sub>[Higher Order Function | Medium](https://medium.com/functional-javascript/higher-order-functions-78084829fff4#.ka4840l1e)</sub>  
<sub>[Functional JavaScript](https://www.safaribooksonline.com/library/view/functional-javascript/9781449360757/ch04.html)</sub>  
<sub>[Functional Programming | Book](http://shop.oreilly.com/product/0636920028857.do)</sub>  
<sub>[Higher-Order Functions and Function Binding | Explained exercise](http://clarkfeusier.com/2015/01/11/interview-question-function-bind.html)</sub>

Las [Higher Order Functions](http://eloquentjavascript.net/05_higher_order.html) son aquellas funciones que aceptan otras funciones como parametros o que devuelven funciones ([o las 2 cosas](http://jtfmumm.com/blog/2013/08/31/nested-higher-order-functions-in-javascript/)). Son aquellas funciones que tratan a otras funciones como valores (de entrada o de salida)

Existe un paradigma 

Aplicados a javascript, unos principios basicos de esta [programación funcional](http://www.smashingmagazine.com/2014/07/dont-be-scared-of-functional-programming/) serian:

- Todas tus funciones deben aceptar al menos 1 argumento
- Todas tus funciones deben devolver un valor u otra funcion
- No for-loops

Los arrays disponen [a traves de su prototipo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Methods_2) algunas _higher order functions_  MUY utilizadas.

Las nativas para `array` son entre otras:

###[forEach()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

`forEach()` nos permite ejecutar una función sobre cada elemento del array

```javascript
function logArrayElements(element, index, array) {
  console.log('a[' + index + '] = ' + element);
}

// Note elision, there is no member at 2 so it isn't visited
[2, 5, , 9].forEach(logArrayElements);
// logs:
// a[0] = 2
// a[1] = 5
// a[3] = 9
[]
```


### [pluck()](http://underscorejs.org/#pluck), [zip()](http://underscorejs.org/#zip), [reject()](http://underscorejs.org/#reject), [groupBy()](https://lodash.com/docs#groupBy), [sample()](https://lodash.com/docs#sample), [chunk()](https://lodash.com/docs#chunk), [flatten()](https://lodash.com/docs#flatten)...

Utilizando librerias externas (como [underscore](http://underscorejs.org/#collections) o [lodash](https://lodash.com/docs)) tendremos disponibles en nuestro código muchas más _higher order functions_ que nos facilitaran el trabajo
