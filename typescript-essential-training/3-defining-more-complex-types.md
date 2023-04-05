<div align="center">
   <h1>:woman_technologist: Defining More Complex Types :woman_technologist:</h1>
</div>

<h1>Combining Multiple Types with Union Types</h1>

- Can define multiple type aliases that create new, more dynamic and more powerful Types
- Can update to allow multiple types using the pipe syntax, can provide as many Types as you want to support

<h3>Example 1</h3>

```typescript
interface Contact {
	id: number
	name: ContactName 
	birthDate?: Date | number | string
	status?: ContactStatus
}
```

- Can use a type alias for multiple Types

<h3>Example 2</h3>

```typescript
type contactBirthDame = Date | number | string

interface Contact {
	id: number
	name: ContactName 
	birthDate?: ContactBirthDame
	status?: ContactStatus
}
```

- Another use is to combine multiple types together to make a total new Type
- Unlike the Pipe Syntax which combines alternate Types, using the Ampersand syntax combines the two Types together to create an entirely new type

<h3>Example 3</h3>

```typescript
interface Contact {
	id: number
	name: ContactName 
	birthDate?: ContactBirthDame
	status?: ContactStatus
}

Interface Address {
	line1: string
	line2: string
state: string
county: string
postalCode: string
}

Type AddressableContact = Contact & Address
```

- Type aliases much more effect than enums in some cases, because enums add more code, while type aliases can restrict certain values to a field more effectively 

<h3>Example 4</h3>

```typescript
type ContactStatus = “active” | “inactive” | “new”
```

<h1>Keyof Operator</h1>


- Can be used to reference fields of a given type

<h3>Example 5</h3>

```typescript
Type ContactFields = keyof Contact
```

- This is say that a variable of this type may only contain values matching the names of the properties on the Type
- This includes any fields now as well as any fields we may reference in the future
- Much like Union Types, they are only available at compile time and actually compiled into your running code, not available at runtime

<h3>Example 6</h3>

```typescript
function getValue(source, propertyName: keyof Contact) {
	return source[propertyName]
}
```

- Keyof limits the values of the parameter to valid property names of the Type, TypeScript can quickly highlight mistakes as invalid values
- Has nothing to do with the Types specifically, so sometimes refactoring to a Generic function can make sense

<h3>Example 7</h3>

```typescript
function getValue<T>(source: T, propertyName: keyof T) {
	return source[propertyName]
}
```

- You can pass in any type for the target object, and TypeScript can readjust to ensure the second parameter so that it is a property name of the first parameter’s Type, no matter what the Type may be 

<h3>Example 8</h3>

```typescript
function getValue<T, U extends keyof T>(source: T, propertyName: U) {
	return source[propertyName]
}
```

- A second Type has been introduced that be referred later in the function, this also makes it a cleaner version of the function

<h1>Typeof Operator</h1>


- A JavaScript feature that been around for a long time
- Although we can understand what the parameter should be, TypeScript can’t. Static Typing can be added to fix this
- When the Type is specified, TypeScript can make much smarter inferences with `typeof`
- TypeScript also also allows you to use `typeof` to define static Types dynamically

<h3>Example 9</h3>

```typescript
const myType = { min: 1, max: 200 }

function save(source: typeof myType) {}
```

- Can be used to refer to the same Type later
- Can make sure that anytime some tries to call a function, the parameter can match the same structure as what is defined in the variable
- An explicit Interface or Type Alias can do this in most cases, but sometimes typeof is a helpful shortcut
- Can be useful when writing dynamic code that accepts values of types you don’t know about until runtime


