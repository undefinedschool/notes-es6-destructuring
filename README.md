# ✨ ES6: Array & Object destructuring

- Es una forma concisa de _extraer valores_ de _arrays_ y otros _objetos_ y guardarlos en variables

## Object destructuring

:warning: el **orden** de los elementos **no importa**, sólo que _matcheen_ los nombres de las propiedades

```js
// before destructuring 😢
const name = user.fullName;
console.log(name); // 'Sam Fisher';

// after destructuring 😍
const { fullName } = user;
console.log(fullName) // 'Sam Fisher';
```

```js
// The old way 😱
const fullName = user.fullName;
const age = user.age;
const job = user.job;
console.log(fullName, age, job); // 'Sam Fisher' 62 'spy'

// The destructuring way 😎
const { fullName, age, job } = user;
console.log(fullName, age, job); // 'Sam Fisher' 62 'spy';
```

## Extraer valores de objetos pasados como parámetros de una función

```
// ES5
function myFunc(opts) {
  var name = opts.name;
  var age = opts.age;
}

myFunc({ name: 'John', age: 25 });
```

```
// ES6
function myFunc({ name, age }) {}
```

## Renombrar valores extraídos (aka _alias_, _custom names_)

```
function myFunc({ someLongPropertyName: prop }) {
  console.log(prop);
}

myFunc({ someLongPropertyName: 'Hello' })
// logs 'Hello'
```

## Default values

```js
const { name = 'Sam' } = user;
console.log(name); // Sam
```

## Arrays

:warning: el **orden** de los elementos **importa**

```js
const array = [1, 2, 3, 4, 5];
const [one, two] = array;

console.log(one, two);
```

```js
// skip some numbers
const array = [1, 2, 3, 4, 5];
const [,, three] = array;

console.log(three);
```

### Swapping

```js
// element swapping without aux ✨
let a = 1;
let b = 2;

[a, b] = [b, a];

console.log(a);
console.log(b);
```

### Destructuring + Spread magic ✨

:warning: para que esto funcione, el _spread operator_ sólo puede asignarse al último elemento al que aplicamos _destructuring_

```js
const numbers = [ 10, 20, 30, 40, 50 ];
const [ head, ...tail ] = numbers;
```
