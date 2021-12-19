# React 1


## ES6 Overview
- ES6: ECMAScript 2015
- var: function scope, let: block scope, const: block scope
- const: cannot be redeclared or reassigned, but can be mutable. 
- Example of arrow function:
```
let func = (a) => {} // parentheses optional with one parameter
let func = (a, b, c) => {} // parentheses required with multiple parameters
```
- Example of template literal in ES6:
```
let str = `Release Date: ${date}`let str = `Release Date: ${date}`
```
- Return keyword implied when using arrow functions without curly braces:
```
let func = (a, b, c) => a + b + c // curly brackets must be omitted
```
- Shorthand for assigning properties to variables of the same name:
```
let obj = {
  a,
  b,
}
```

## React
- Small react example:
```
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);
```
- ^ displays a heading saying Hello, world!
- Example of JSX syntax:
```
const element = <h1>Hello, world!</h1>;
```
- JSX produces React “elements”.
- Example of embedding expressions in JSX:
```
const name = 'Anas';
const element = <h1>Hello, {name}</h1>;

ReactDOM.render(
  element,
  document.getElementById('root')
);
```
- Example of using JSX inside if statement:
```
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```
- Safe to embed user input with JSX:
```
const title = response.potentiallyMaliciousInput;
// This is safe:
const element = <h1>{title}</h1>;
```
- React DOM escapes values embedded in JSX before rendering them. 
- Example of rendering a react element into a root DOM node: 
```
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```
- React elements are immutable. 
- React will only update what is necessary. 
- Example of rendering a component:
```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);
```
- Name props from the component’s own point of view rather than the context in which it is being used.
- State is similar to props, but it is private and fully controlled by the component.
- Lifecycle methods: componentDidMount() and componentDidMount().
- Example of handling event in React:
```
<button onClick={activateLasers}>
  Activate Lasers
</button>
```