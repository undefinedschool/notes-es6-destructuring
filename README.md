> El siguiente contenido fue elaborado por [@_nhsz](https://twitter.com/_nhsz) como guía para las clases de [undefined school](https://twitter.com/undefinedSchool)

> Son bienvenidos los _issues_ y _PRs_ para mejorar el contenido, corregir errores, etc

# ✨ ES6: Array & Object destructuring

👉 Es una forma concisa de _**extraer valores individuales**_ (_"desestructurar"_) de _arrays_ y otros _objetos_ y guardarlos en variables.

## Object destructuring

Usando _destructuring_, vamos a crear variables con los mismos nombres que las propiedades del objeto y guardar en estas sus valores.

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

Los nombres que usemos para los parámetros deben coincidir con nombres de propiedades del objeto que se recibe, sino van a tener `undefined` como valor

```js
// ES5
function myFunc(opts) {
  var name = opts.name;
  var age = opts.age;
}

myFunc({ name: 'John', age: 25 });
```

```js
// ES6
function myFunc({ name, age }) {
  // your code ✨
}
```

## Renombrar valores extraídos (aka _alias_/_custom names_)

### En parámetros recibidos en funciones

```js
function myFunc({ someLongPropertyName: prop }) {
  console.log(prop);
}

myFunc({ someLongPropertyName: 'Hello' })
// logs 'Hello'
```

### Extrayendo valores a constantes/variables

```js
const user = {
  fullName: 'Sam Fisher',
  age: 62,
  job: 'spy'
}

const { fullName } = user;
fullName;     // =>'Sam Fisher'

// assign `completeName` alias to `fullName` bind
const { fullName: completeName } = user;
completeName; // => 'Sam Fisher'
```

## Default values

```js
const { name = 'Sam' } = user;
console.log(name); // Sam
```

## Arrays

:warning: el **orden** de los elementos **importa**

```js
// without destructuring 😱
const array = [1, 2, 3, 4, 5];

const one = array[0];
const two = array[1];
```

En vez de definir variables, lo que hacemos con _destructuring_ es crear un _array de variables_. El índice de estas variables se corresponde con el índice de los elementos en el array que estamos mapeando.

```js
// with destructuring 😎
const array = [1, 2, 3, 4, 5];
// `one` will take the array[0] value and `two` the array[1] value
const [one, two] = array;

console.log(one, two);
```

```js
// skip some numbers
const array = [1, 2, 3, 4, 5];
const [,, three] = array;

console.log(three);
```

### Retornar y extraer múltiples valores

```js
const sumAndMultiply = (a, b) => [a + b, a * b];

const [sum, product] = sumAndMultiply(2, 3);
```

### Swapping de variables

```js
// element swapping without aux ✨
let a = 1;
let b = 2;

[a, b] = [b, a];

console.log(a);
console.log(b);
```

### Destructuring + Rest parameters magic ✨

También podemos quedarnos con el primer valor de un _array_ usando _destructuring_ y guardar el resto en otro _array_. El `rest operator` (`...`) nos permite referenciar a estos elementos restantes.

:warning: para que esto funcione, el operador de los 3 `...` (similar a cuando usamos _spread_, pero en este caso lo llamamos _rest parameters_) sólo puede asignarse al último elemento al que aplicamos _destructuring_ (porque es el *rest*o, lo *rest*ante, *rest*... se entiende? [Acá](https://javascript.info/rest-parameters-spread-operator#rest-parameters) podés leer más sobre _rest parameters_)

```js
const numbers = [ 10, 20, 30, 40, 50 ];
// array destructuring + rest operator
const [ head, ...tail ] = numbers;
```

#### Y con objetos

Podemos usar el `rest operator` para crear un objeto con las _propiedades restantes_.

```js
const eBook = { 
  title: 'The Lord of the Rings - The Fellowship of the Ring', 
  genre: 'Fantasy', 
  author: 'J. R. R. Tolkien', 
  cover: 'https://i.imgur.com/OwMUnQu.jpg'
}

const {title, ...info} = eBook;
```

En el ejemplo anterior, el objeto `info` sería equivalente a

```js
const info = {
  genre: 'Fantasy', 
  author: 'J. R. R. Tolkien', 
  cover: 'https://i.imgur.com/OwMUnQu.jpg'
}
```

## Compatibilidad en los diferentes browsers

La sintaxis de _destructuring_ funciona en todos los navegadores modernos (incluyendo mobile), pero **no tiene soporte en IE**.

El `rest operator` **no funciona en Edge ni Safari** (aunque Edge tendrá soporte cuando salga la beta con Chromium).

**No podemos usar [polyfills](https://developer.mozilla.org/en-US/docs/Glossary/Polyfill)** con _destructuring_
