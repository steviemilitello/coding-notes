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

<h1>Indexed Access Types</h1>


- Used to determine the Type of a certain property or multiple properties of a target object
- Same as JavaScript syntax for accessing a property of an object using the index syntax

<h3>Example 10</h3>

```typescript
type Awesome = Contact[“id”]
```

- Types happen to be the same, but no different connection between the two

<h3>Example 11</h3>

```typescript
type Awesome = Contact[“id”]

Interface ContactEvent {
           contactId: Contact[“id”]

interface ContactDeletedEvent extends ContactEvent {
}

Interface ContactStatusChangedEvent extends ContactEvent {
          oldStatus: Contact[“status”]
          newStatus: Contact[“status”]
}

Interface ContactEvents {
         deleted : ContactDeletedEvent
         statusChanged: ContactStatusChangedEvent
         // …. And so on
}
```

- Not only can use this syntax to reference the properties, but the properties of those properties

<h3>Example 12</h3>

```typescript
type Awesome = Contact[“id”][“postalcode”]
```

- TypeScript can determine the Type of the parameter even if not specified in a call if index access is used
- TypeScript is also smart enough to figure out the Types inside the method as well
- Can help product powerful and advanced Type checking

<h3>Example 13</h3>

```typescript
function getValue<T, U extends keyof T>(source: T, propertyName: U) {
	return source[propertyName]
}

function handleEvent<T extends keyof ContactEvents>(
           eventName: T
           handler: evt: ContactEvents[T] => void
) {
           if (eventName === “statusChanged”) {
                    handler({contactId: 1, oldStatus: “active”, newStatus: “inactive” } as ContactDeletedEvent)
       }

}

handleEvent(“statusChanged”, evt => evt)

```

<h1>Defining Dynamic But Limited Types with Records</h1>


- Useful when you want to extend an object with properties that don’t exist on the Type that TypeScript originally inferred
- Defining a variable with the any Type is opting out of Type safety all together
- There is a TypeScript configure setting that allows you to trigger a compile error whenever any is applied
- When alternative you can apply to still retain some of the flexibility and dynamism of the any type is the record type
- The `record` type is a flexible Type structure that allows you to define some structure and even some Typing without having to detail everything possible property of the type you’re trying to describe
- Record is a Generic syntax with two parameters. The first is the possible property values while the second is the possible property types
- Can add a union to add to the second parameter

<h3>Example 14</h3>

```typescript
let x: Record<string, string | number | boolean | Function> = { name: “Bruce Wayne” }
x.number = 1234
x.active = “true”
x.log = () => console.log(“awesome!”)

```






