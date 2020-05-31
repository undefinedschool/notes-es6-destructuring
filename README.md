# ![ES6: Array & Object destructuring](https://i.imgur.com/jmOquTu.png)

<div align="center">  
  <p align="center">
  <sub>Hola! Soy Nico (<strong>nhsz</strong>), <strong>Dev Full Stack JavaScript y mentor</strong>.</sub>
  </p>
  
  <p align="center">
    <sub>
      Hace un tiempo (principios de 2019) empecé un proyecto llamado <a href="https://undefinedschool.io"><strong>undefined school</strong></a>, una <strong>escuela de Desarrollo Web Full Stack JavaScript</strong>, 100% Open Source, con mentorías personalizadas para grupos reducidos y el foco puesto en los <strong>fundamentos</strong> y <strong>conceptos avanzados</strong>.
    </sub>
  </p>

  <p align="center">
    <sub>
      Me interesa mucho la intersección entre la educación y la tecnología, por eso también participo en proyectos como <a href="https://freecodecampba.org">freeCodeCampBA</a> (co-founder y co-organizador) y <a href="https://twitter.com/LXBA_">Learning Experience BA</a> (co-founder y co-organizador).
    </sub>
  </p>

 <p align="center">
    <sub>
  👉 Si estás arrancando en el mundo del desarrollo web y necesitás una mano, podés encontrarme en <a href="https://twitter.com/_nhsz/">Twitter</a> (también para hablar sobre cualquier tema relacionado a JavaScript o <em>#nerdeadas</em> en general 😛).
  </sub>
  </p>
  
  <p align="center">
  <sub>
    Por último, te cuento que soy muy fan del café (obvio que negro y sin azúcar), asi que si las notas te resultaron útiles y querés colaborar para que no me quede dormido y siga escribiendo guías, apuntes y más <strong>contenido Open Source en español</strong>, podés invitarme uno, gracias! ❤️
  </sub>
  </p>
  
  <p align="center">
  ☕
  <code> 
  <a href="https://cafecito.app/nhsz">
    <strong>Invitame 1 café!</strong>
  </a>
  </code>
  </p>
  <hr>
</div>

👉 Ver [todas las notas](https://github.com/undefinedschool/notes)

## Contenido

- [Intro](https://github.com/undefinedschool/notes-es6-destructuring-notes#intro)
- [Object destructuring](https://github.com/undefinedschool/notes-es6-destructuring-notes#object-destructuring)
  - [Extraer valores de objetos pasados como parámetros de una función](https://github.com/undefinedschool/notes-es6-destructuring-notes#extraer-valores-de-objetos-pasados-como-par%C3%A1metros-de-una-funci%C3%B3n)
  - [Renombrar valores extraídos (aka alias/custom names)](https://github.com/undefinedschool/notes-es6-destructuring-notes#renombrar-valores-extra%C3%ADdos-aka-aliascustom-names)
    - [En parámetros recibidos en funciones](https://github.com/undefinedschool/notes-es6-destructuring-notes#en-par%C3%A1metros-recibidos-en-funciones)
    - [Extrayendo valores a constantes/variables](https://github.com/undefinedschool/notes-es6-destructuring-notes#extrayendo-valores-a-constantesvariables)
- [Default values](https://github.com/undefinedschool/notes-es6-destructuring-notes#default-values)
- [Arrays](https://github.com/undefinedschool/notes-es6-destructuring-notes#arrays)
  - [Retornar y extraer múltiples valores](https://github.com/undefinedschool/notes-es6-destructuring-notes#retornar-y-extraer-m%C3%BAltiples-valores)
  - [Swapping de variables](https://github.com/undefinedschool/notes-es6-destructuring-notes#swapping-de-variables)
- [Destructuring + Rest parameters magic ✨](https://github.com/undefinedschool/notes-es6-destructuring-notes#destructuring--rest-parameters-magic-)
  - [...y con objetos](https://github.com/undefinedschool/notes-es6-destructuring-notes#y-con-objetos)
- [Compatibilidad con los diferentes browsers](https://github.com/undefinedschool/notes-es6-destructuring-notes#compatibilidad-con-los-diferentes-browsers)

---

## Intro

Es una forma concisa de _**extraer valores individuales**_ (_"desestructurar"_) de _arrays_ y otros _objetos_ y guardarlos en variables.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)

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

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)

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

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)

## Renombrar valores extraídos (aka _alias_/_custom names_)

### En parámetros recibidos en funciones

```js
function myFunc({ someLongPropertyName: prop }) {
  console.log(prop);
}

myFunc({ someLongPropertyName: 'Hello' })
// logs 'Hello'
```

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)

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

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)

## Default values

El _destructuring_ nos permite asignar _valores por default_ a una variable, en el caso de que no reciba ningún valor ó este sea `undefined`.

```js
const { name = 'Sam' } = user;
console.log(name); // Sam
```

También funciona con arrays

```js
const array = [1];

const [one, two = 2] = array;
```

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)

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

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)

### Retornar y extraer múltiples valores

```js
const sumAndMultiply = (a, b) => [a + b, a * b];

const [sum, product] = sumAndMultiply(2, 3);
```

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)

### Swapping de variables

```js
// element swapping without aux ✨
let a = 1;
let b = 2;

[a, b] = [b, a];

console.log(a);
console.log(b);
```

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)

## Destructuring + Rest parameters magic ✨

También podemos quedarnos con el primer valor de un _array_ usando _destructuring_ y guardar el resto en otro _array_. El `rest operator` (`...`) nos permite referenciar a estos elementos restantes.

:warning: para que esto funcione, el operador de los 3 `...` (similar a cuando usamos _spread_, pero en este caso lo llamamos _rest parameters_) sólo puede asignarse al último elemento al que aplicamos _destructuring_ (porque es el *rest*o, lo *rest*ante, *rest*... se entiende? [Acá](https://javascript.info/rest-parameters-spread-operator#rest-parameters) podés leer más sobre _rest parameters_)

```js
const numbers = [ 10, 20, 30, 40, 50 ];
// array destructuring + rest operator
const [ head, ...tail ] = numbers;
```

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)

### ...y con objetos

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

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)

## Compatibilidad con los diferentes browsers

La sintaxis de _destructuring_ funciona en todos los navegadores modernos (incluyendo mobile), pero **no tiene soporte en IE**.

El `rest operator` **no funciona en Edge ni Safari** (aunque Edge tendrá soporte cuando salga la beta con Chromium).

**No podemos usar [polyfills](https://developer.mozilla.org/en-US/docs/Glossary/Polyfill)** con _destructuring_.

👉 Como siempre, se recomienda visitar [Can I use...](https://caniuse.com/#search=destructuring) para estar al tanto de las novedades en cuanto al soporte de una determinada feature.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-es6-destructuring-notes#contenido)
