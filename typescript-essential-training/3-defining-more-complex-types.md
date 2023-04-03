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

