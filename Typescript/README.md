# TypeScript Notes

## Introduction
TypeScript offers all of JavaScript’s features, and an additional layer on top of these: TypeScript’s type system. The main benefit of TypeScript is that it can highlight unexpected behavior in your code, lowering the chance of bugs.

## Types

### Javascript
* `boolean`
* `bigint`
* `null`
* `number`
* `string`
* `symbol`
* `undefined`

### TypeScript
* `any` allow anything
* `unknown` ensure someone using this type declares what the type is
* `never` it’s not possible that this type could happen
* `void` a function which returns undefined or do not return anything.

## Types by Inference
Assigned value is used to determine the type of variable.
```
let helloWrold = 'hello world'; // This is auto assigned string type => let helloworld: string = ''
```

## Object Type
You can explicitly describe this object’s shape using an `interface` declaration:
```
interface User {
  name: string;
  id: number;
}

const user: User = {
  name: "Hayes",
  id: 0,
};
```

## Usage with Classes
Since JavaScript supports classes and object-oriented programming, so does TypeScript. You can use an interface declaration with classes:
```
interface User {
  name: string;
}
 
class UserAccount {
  name: string;
 
  constructor(name: string) {
    this.name = name;
  }
}
 
const user: User = new UserAccount("Murphy");
```

## Function Parameter and Return Types
You can use interfaces to annotate parameters and return values to functions:
```
function update(user: User): User {
  // ...
}
```

## Composing Types

### Unions
With a union, you can declare that a type could be one of many types.
```
type WindowStates = "open" | "closed" | "minimized";
```

### Generics
Generics provide variables to types. A common example is an array. An array without generics could contain anything. An array with generics can describe the values that the array contains.
```
type StringArray = Array<string>;
type NumberArray = Array<number>;
type ObjectWithNameArray = Array<{ name: string }>;

interface Backpack<Type> {
  add: (obj: Type) => void;
  get: () => Type;
}
```

## Structural Type System
One of TypeScript’s core principles is that type checking focuses on the shape that values have. This is sometimes called `duck typing` or `structural typing`. In a structural type system, if two objects have the same shape, they are considered to be of the same type.
```
interface Point {
  x: number;
  y: number;
}
 
function logPoint(p: Point) {
  console.log(`${p.x}, ${p.y}`);
}

const point = { x: 12, y: 26 };
logPoint(point); // it will work as TypeScript will consider point as Point Type as they are same

class VirtualPoint {
  x: number;
  y: number;
 
  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}
 
const newVPoint = new VirtualPoint(13, 56);
logPoint(newVPoint); // This will work too as TypeScript will consider this class Type to be same as Point type.
```