# 3 JavaScript

## Indice

- [Variables](#31-variables)
    - [let](#311-let)
    - [const]()
    - [var [no recomendado]]()
    - [Tipos de variables primitivos]()
        - [number]()
        - [string]()
        - [boolean]()
        - [undefined]()
        - [null]()
        - [Function]()
        - [Object]()
        - [Symbol y BigInt]()
- [Condicionales]()
    - [if, else if, else]()
    - [switch case]()
    - [expresiones condicionales]()
    - [declaraciones por defecto]()
- [Bucles]()
    - [while]()
    - [do while]()
    - [for]()
- [Funciones]()
    - [Crear función]()
        - [Funciones normales]()
        - [Funciones flecha]()
    - [Ejecutar funciones]()
    - [Devolver valores]()
    - [Parámetros]()
        - [Parámetros opcionales]()
        - [Parámetros rest]()
- [Arrays]()
    - [Crear Array]()
    - [Leer elementos]()
    - [Añadir elementos]()
    - [Modificar elementos]()
    - [Eliminar elementos]()
    - [Recorrer arrays]()
        - [foreach]()
        - [for i]()
    - [Funciones comunes en arrays]()
        - [push]()
        - [pop]()
        - [unshift]()
        - [shift]()
        - [map]()
        - [filter]()
    - [Crear array a partir de un string]()
- [Set]()
    - [add]()
    - [delete]()
    - [has]()
    - [for of]()
- [Objetos anónimos]()
    - [Clave - valor]()
    - [Guardar valores]()
    - [Obtener valores]()
    - [Crear funciones para nuestro Object]()
        - [set]()
        - [get]()
        - [delete]()
- [Map]()
    - [set]()
    - [get]()
    - [delete]()
- [Try - catch - finally]()

## 3.1 Variables

Una variable es una clave a la que se le asocia un valor en la memoria.

Pongamos que tenemos el valor del nombre de una persona: `David`.

Esta información (por lo general) lo vamos a querer almacenar en la memoria RAM. Por ejemplo en el slot 0x7fff5fbff5ac. El slot 0x7fff5fbff5ac es un espacio de memoria libre que tiene la memoria RAM. El slot puede variar según el momento de la ejecución. Pero esto es solo un ejemplo ficticio.

Nos situamos: ahora tenemos en nuestra memoria RAM un dato con el valor `David`. Todo genial, pero ahora, ¿cómo conseguimos la información que hay almacenada en el slot 0x7fff5fbff5ac?

Para eso nos sirven las variables. Nos permiten asociar a un nombre (clave) una referencia a la memoria RAM, o mejor dicho, un valor.

Cuando nosotros hacemos esto:

```python
nombre = 'David' # Lo que hace el lenguaje es decir: Para cuando yo quiera conseguir el valor de la clave "nombre", el ordenador va a buscar a la memoria RAM la referencia al slot 0x7fff5fbff5ac y el valor asociado es 'David'
```

Todo esto es lo que comúnmente y resumidamente pasa por debajo de las variables. Pero la realidad es que, por lo general, no tenemos en cuenta exactamente en qué slot de memoria se encuentran ubicados los datos. Simplemente nos interesa las claves (el nombre personalizado que le pongamos) y el valor asociado a estas.


En JavaScript, al igual que todos los lenguajes de programación, podemos crear variables. Aunque existen 3 formas: `const`, `let` y `var`

# 3.1.1 Let

La palabra `let` es una palabra reservada propia del lenguaje. ¿Esto qué significa? Que cualquier palabra reservada del lenguaje como `var`, `for`, `while`, `class`, ... son palabras que son exclusivas para ejecutar hacer funcionalidad en el lenguaje de programación, y por ende, no se puede usar para otra cosa que no sea para eso.

En el caso del `let`, es una palabra reservada para la declaración de variables. La sintaxis para declarar variables con `let` es `let clave = valor`.

Ejemplo:
```javascript
let clave = 'valor'; // Válido
let nombre = 'David'; // Válido
let edad = 17; // Válido
let let = 0; // No es válido porque la palabra 'let' es una palabra reservada del lenguaje
animal let = 0; // No es válido porque 'let' debe ir antes que la clave
```

¿Cómo puedo verificar el valor de la variable? Para eso vamos a utilizar una función que se llama `console.log`, que si nos fijamos en la [introducción](./00-que-es-javascript.md#01-ejecutar-hola-mundo) de este repositorio, lo utilizamos para imprimir el `'Hola Mundo!'`. La función `console.log` lo que hace es simplemente mostrar el contenido que le pasamos entre paréntesis en la consola. Contenido puede ser un texto, un número, o incluso variables.

La sintaxis que usaremos para imprimir el contenido en la consola es `console.log(<nuestro contenido>);`.
Ejemplos con texto, números y variables.

```javascript
console.log('Hola Mundo!'); // Imprimirá en la consola: 'Hola Mundo!'
console.log(23); // Imprimirá en la consola: 23
let nombre = 'David'; // Asigna a la variable 'nombre' el valor 'David'
console.log(nombre); // Imprimirá en la consola: 'David'
```

No sé si te habrás fijado, pero en el ejemplo de código anterior habían un par de cosas que no habíamos mencionado. Primero, es posible que hayas notado que todo lo que estaba a la derecha del `//` era del mismo color.

La doble barra lateral (`//`) es un texto reservado dedicado para que todo lo que esté a la derecha sean comentarios en el código. Esto hace que no se ejecute nada a partir de ese texto en cada línea:

```javascript
let clave = 'valor'; // Esto es el comentario y todo lo que ponga aquí nunca se ejecutará
// let nombre = 'David'; Este let nunca funcionará porque está a la derecha de las dos barras laterales e impiden la ejecución de todo lo que esté a la derecha.
```

Adicionalmente, te habrás fijado que justo después del valor, hemos puesto un `;`. ¿Qué es el `;`? ¿Para qué sirve?
Resumidamente: el `;` es un indicador de que se acaba la instrucción actual, lo que nos permite poder dejar más claro la separación de distintas instrucciones. El `;` se pone al final de cada instrucción:

```javascript
// Instrucción 1 - Declarar la variable persona
let persona = 'Antonio';
// Instrucción 2 - Cambiar el valor de la variable persona
persona = 'David';
// Instrucción 1 y 2 en la misma línea:
let persona = 'Antonio'; persona = 'David';
// Estas instrucciones van a fallar porque no hay ningún delimitador:
let persona = 'Antonio' persona = 'David'
```

No es obligatorio poner el `;`, y en este lenguaje, depende de tus gustos personales. En mi caso recomiendo encarecidamente utilizar el `;` ya que añade claridad a cuándo acaban las instrucciones y, adicionalmente, la mayoría de otros lenguajes tienen incluído el `;` de forma obligatoria en su sintaxis.

Otra cosa más, en el ejemplo anterior puedes observar que he `cambiado` el valor de la variable persona.
Esto se llama de distintas maneras (re-asignar un valor a una variable, cambiar valor de una variable, etc).

Pero lo que hace es simplemente que a la misma clave que teníamos creada antes podamos cambiarle el valor que se almacena en la memoria RAM.

```javascript
let nombre = 'David'; // El valor asociado a 'nombre' es 'David'
nombre = 'Antonio'; // El valor asociado a 'nombre' ha cambiado de 'David' a 'Antonio'
```

Para el cambio de variables, no se usa la palabra reservada `let`. Simplemente se pone `clave = valor;` directamente.

Información adicional que tocaremos más tarde:
- El `scope` del `let` es a nivel de bloque (veremos lo que significa en el apartado del `var`).
- Las variables creadas con `let` son mutables (se puede cambiar el valor asociado a estas).

Más información:
- [Let - JavaScript | MDN](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/let)