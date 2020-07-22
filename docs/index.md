ESLint configuration for modern JavaScript that improves code quality by removing bad features and preventing anti-patterns

## Use new replacements of problematic features

### Replace constructor functions with classes

```js
// bad
function Animal() {}
Animal.prototype.speak = function () {
  return this;
};

// good
class Animal {
  speak() {
    return this;
  }
}
```

### Replace globals with ES/CJS modules

The ES module standard makes it easy to safely reuse JavaScript code across files without leaking into the global scope, and enables useful tooling features like tree shaking and loaders. CJS modules can also be used with Node, though they're not as analyzable and flexible with build tools.

```js
// bad
window.greeting = "Hello, world!";

// good (ES)
export const greeting = "Hello, world!";

// good (CJS)
exports.greeting = "Hello, world!";
```

### Replace `var` with `let`/`const`

Variables created with `var` are hoisted to the nearest function, which can cause confusing behavior with the order of accessing variables and variables overriding each other in nearby scopes. `let` and `const` replace `var` with more predictable block scoping (typical with other programming languages). `const` should be preferred if you don't need to reassign the variable, otherwise use `let`.

```js
// bad
var greeting = "Hello, world!";
var enabled = true;
enabled = false;

// good
const greeting = "Hello, world!";
let enabled = true;
enabled = false;
```

### Replace string concatenation with template literals

`+` can have ambiguous behavior if it's used between strings and numbers interchangeably. To avoid bugs and unwanted formatting, it's better to use template literal syntax (which also allows for custom templates) for strings and exclusively use `+` for math.

```js
// bad
const name = "world";
console.log("Hello, " + name + "!");

// good
const name = "world";
console.log(`Hello, ${name}!`);
```

### Replace the `arguments` keyword with spread arguments

`arguments` used to be the only way to get a variable number of arguments from a function dynamically, but it isn't supported in arrow functions and confusingly is not an actual Array object. The spread argument (`...`) solves this issue and works with both `function` and arrow functions.

```js
// bad
function joinWords() {
  return Array.from(arguments).join(" ");
}

// good
function joinWords(...args) {
  return args.join(" ");
}
```
