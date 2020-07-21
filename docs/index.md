<section>

## Legacy syntax

Out with the old...

### Constructor functions

```js
function Animal() {}

Animal.prototype.speak = function () {
  return this;
};
```

### Globals

```js
window.greeting = "Hello, world!";
```

### `var`

```js
var greeting = "Hello, world!";

var enabled = true;
enabled = false;
```

### String concatenation

```js
const name = "world";
console.log("Hello, " + name + "!");
```

### `arguments`

```js
function joinWords() {
  return Array.from(arguments).join(" ");
}
```

</section>

<section>

## Recommended syntax

...and in with the new!

### Classes

```js
class Animal {
  speak() {
    return this;
  }
}
```

### ES/CJS modules

```js
export const greeting = "Hello, world!";
```

### `let/const`

```js
const greeting = "Hello, world!";

let enabled = true;
enabled = false;
```

### Template literals

```js
const name = "world";
console.log(`Hello, ${name}!`);
```

### Spread arguments

```js
function joinWords(...args) {
  return args.join(" ");
}
```

</section>
