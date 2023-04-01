<div align="center">
   <h1>:woman_technologist: Basic TypeScript Usage :woman_technologist:</h1>
</div>

<h1>Primitives and Built-in-Types</h1>

- Type inference by hovering over the variable. Cannot be done if assignment is not present.
- Colon followed by the name of the type to define type
	- ex. `let x: number = 5`  or  `let y: string` or   `let z: boolean`
- Can even identify array types such as l`et a: Date` or `let b: string[]`
- If you try assignment variable to value of wrong type, TypeScript will give you errors
- Any type, When you want to assignment a different type to existing variable
	- example: `let b: any`
- Can use Type Casting to treat any value as any
	- example: `b = “Hello!”` as any
- Any type has a significant downside - It tells TypeScript to not include the Type in Type Checking, which goes against the point of using TypeScript in the first place

<h1>Creating Custom Types with Interfaces</h1>


- To define an interface, use the keyword `interface` followed by the name and double brackets
- Similar to Class syntax in JavaScript. Any Class definitions using JavaScript syntax can also be used as Interfaces
- Class vs. Interface - Interfaces solely exist to provide Type information to TypeScript. Only used at Compile Time, Never available nor will appear in runtime code.

<h3>Example 1</h3>

```typescript
interface Contact {
	id: number
	name: string 
	birthDate: Date
}
```

- Once defined, can be used like any build in type 
- Because it is defined as `Contact`, TypeScript is able to provide fields in autoselect

<h3>Example 2</h3>

```typescript
Let primaryContact: Contact = {
	id: 12345
	name: “Jamie Johnson”
	birthDate: new Date(“01-01-1980”)
}
```

- Allows us to append as optional by appending a question mark in the interface definition
- Still enforces Typing in field

<h3>Example 3</h3> 

```typescript
interface Contact {
	id: number
	name: string 
	birthDate?: Date
}
```

- Multiple interfaces can be combined to create brand new ones
- Can be merged with extends keyword

<h3>Example 4</h3> 

```typescript
Interface Address {
	line1: string
	line2: string
state: string
county: string
postalCode: string
}

interface Contact extends Address {
	id: number
	name: string 
	birthDate?: Date
}
```

- Can now assign fields to objects

<h3>Example 5</h3>

```typescript
Let primaryContact: Contact = {
	id: 12345
	name: “Jamie Johnson”
	birthDate: new Date(“01-01-1980”)
postalCode: 11111 
}
```

