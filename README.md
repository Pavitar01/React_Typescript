<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
<img src="https://i.ytimg.com/vi/1jMJDbq7ZX4/maxresdefault.jpg" width={100}  class="image"/>


# Getting Started React With Typescript
``` bash
TypeScript is JavaScript with syntax for Types
```
# Why
<h5> 1. Type Safety</h5>

``` bash 
TypeScript introduces static typing, allowing developers to define types for variables, function parameters, and return values.
```
<h5>2. Code Quality </h5>

``` bash
With type annotations, code becomes more self-documenting and easier to understand.
```

<h5>3. Early Error Detection</h5>

``` bash
The TypeScript compiler can catch common mistakes and type mismatches during development.
```

<h1>
    Setup
</h1>
<p>In Terminal </p>

 ``` bash 
npx create-react-app my-app --template typescript
```

# Pre-requisites

<h2>Type Alias </h2>

``` bash
A type alias is a shorthand name for an existing data type in programming.
```
<h5>Example</h5>

``` bash
type User={
name:string,
roll_number:number
}
```
<h5> Like if We Are creating one Object of name user, Now We are assigning its type using type alias (User) </h5>

``` bash
const user:User={
name:"Pavi",
roll_number:10
}
```

# Do we have to capitalize the first letter of a type alias

<p>
    No, it's not necessary to capitalize the first letter of a type alias. While it's a common convention to use capitalization for type names to distinguish them from variables or functions, there's no strict rule that enforces this. You can choose whether or not to capitalize the first letter of your type alias based on your project's coding style and guidelines.
</p>

<h3>We can Also use single alias fo multiple types </h3>

``` bash
type uid= number | string

const user_id : uid = "123"
const user_id : uid = 123

```
<h3>Narrowing</h3>

``` bash
type uid:number | string;

const val=(uid)=>{

if(typeof uid === 'string'){

console.log(uid.toUpperCase);
}
console.log(uid)

}

uid("1234");

```
<h3>Generics</h3>
<p>Generics are like placeholders for data types in code that help you write functions and structures that work with various types while keeping things safe and flexible.</p>

``` bash
// Let's create a simple function that echoes back whatever value is passed to it.


function echo<T>(value: T): T {
    return value;
}

// Usage
// these below values,infered the placeholder type
const result1 = echo("Hello, world!"); // result1 will be of type string
const result2 = echo(42);              // result2 will be of type number

console.log(result1); // Output: Hello, world!
console.log(result2); // Output: 42


```

<h3>Assertion</h3>
<p>Assertion in programming, particularly in TypeScript, is a way to confidently declare the type of a value, overriding the compiler's automatic type inference when needed.</p>

``` bash
let value: any = "12345"; // The type of 'value' is 'any'

// Using type assertion
let length: number = (<string>value).length; // Angle bracket syntax
let length2: number = (value as string).length; // 'as' keyword syntax

console.log(length); // Output: 5
console.log(length2); // Output: 5

```


<h2>Interface </h2>
<p>An interface in programming is often used to define the shape or contract that classes must adhere to, specifying which methods they should implement. So, your statement is accurate in highlighting the concept of defining a "shape" through an interface.e</p>

``` bash
interface Book{

name:string;
author:string;
price:number;

}


const book : Book{

name: "Good Man",
author:"nova",
price:123
}

```
<h5>
TypeScript features for interface
</h5>

<h3>extends </h3>
<p>
this is used to indicate that a class or interface is inheriting or extending the functionality of another class or interface. This allows the new class or interface to inherit the properties, methods, and behavior of the class or interface it is extending, promoting code reuse and hierarchy in your codebase.
</p>

``` bash
interface Book2 extends book{
pages:number;
}

const book2:Book2{
author:"nova",
price:123,
pages:89
}
```


# ReactJs With TypeScript

<h3> App.tsx</h3>

``` bash
import React, { useState } from 'react';
import Counter from './Counter';

const App: React.FC = () => {
  const [count, setCount] = useState<number>(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <h1>React Counter Example</h1>
      <Counter count={count} onIncrement={increment} />
    </div>
  );
};

export default App;


```

<h3>Counter.tsx</h3>

``` bash
import React from 'react';

interface CounterProps {
  count: number;
  onIncrement: () => void;
}
// type CounterProps= {
//   count: number;
//   onIncrement: () => void;
// }


const Counter: React.FC<CounterProps> = ({ count, onIncrement }) => {
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={onIncrement}>Increment</button>
    </div>
  );
};

export default Counter;

```


</body>
</html>
