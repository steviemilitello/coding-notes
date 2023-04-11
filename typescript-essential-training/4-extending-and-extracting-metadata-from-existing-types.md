<div align="center">
   <h1>:woman_technologist: Extending and Extracting Metadata from Existing Types :woman_technologist:</h1>
</div>

<h1>Extending and Modifying Existing Types</h1>

- Utility types that allow you to extend from existing Types, like record, but pick and choose which properties you want to include and exclude in your new Type

<h1>Utility Types</h1>

<h3>Partial Helper</h3>

- A Generic Type
- Creates a new Type that looks exactly like the Type it wraps but with all of its properties defined as optional
- This means you can define as many or as few of them as you wish

<h3>Example 1</h3>

```typescript
type ContactQuery = Partial<Record<keyof Contact, Query>>

function searchContacts(contacts: Contact[], query: ContactQuery) {
    return contacts.filter(contact => {
        for (const property of Object.keys(contact) as (keyof Contact)[]) {
            // get the query object for this property
            const propertyQuery = query[property]
            // check to see if it matches
            if (propertyQuery && propertyQuery.matches(contact[property])) {
                return true
            }
        }

        return false
    })
}

const filteredContacts = searchContacts(
    [/* contacts */],
    {
        id: { matches: (id) => id === 123 },
        name: { matches: (name) => name === "Carol Weaver" },
    }
)
```


<h3>Omit Helper</h3>

- Generic Type that wraps another type and copies that type’s definition and allows you to omit certain properties from that cloned definition
- Restricts Usage of certain properties, opposite of the Partial Helper Type
- Unlike `Partial`, it requires second Generic parameter, the list of property names you’d like to omit

<h3>Example 2</h3>

```typescript
type ContactQuery = Omit<
           Partial<
                Record<keyof Contact, Query>
            >,
           “address” | “status”
>

function searchContacts(contacts: Contact[], query: ContactQuery) {
    return contacts.filter(contact => {
        for (const property of Object.keys(contact) as (keyof Contact)[]) {
            // get the query object for this property
            const propertyQuery = query[property]
            // check to see if it matches
            if (propertyQuery && propertyQuery.matches(contact[property])) {
                return true
            }
        }

        return false
    })
}

const filteredContacts = searchContacts(
    [/* contacts */],
    {
        id: { matches: (id) => id === 123 },
        name: { matches: (name) => name === "Carol Weaver" },
    }
)
```


<h3>Pick Helper</h3>

- Opposite of `Omit`
- Creates a new Type using only the properties named by its second Generic parameter

<h3>Example 3</h3>

```typescript
type ContactQuery = Omit<
           Partial<
                Pick<
                Record<keyof Contact, Query>,
                “id” | “name”
                >
            >

function searchContacts(contacts: Contact[], query: ContactQuery) {
    return contacts.filter(contact => {
        for (const property of Object.keys(contact) as (keyof Contact)[]) {
            // get the query object for this property
            const propertyQuery = query[property]
            // check to see if it matches
            if (propertyQuery && propertyQuery.matches(contact[property])) {
                return true
            }
        }

        return false
    })
}

const filteredContacts = searchContacts(
    [/* contacts */],
    {
        id: { matches: (id) => id === 123 },
        name: { matches: (name) => name === "Carol Weaver" },
    }
)
```


<h3>Required</h3>

- Opposite of `Partial`
- Turns all properties of a type into required properties, instead of optional

<h3>Example 4</h3>

```typescript
type ContactQuery = Omit<
           Partial<
                Pick<
                Record<keyof Contact, Query>,
                “id” | “name”
                >
            >

Type RequiredContactQuery = Required<ContactQuery>

function searchContacts(contacts: Contact[], query: ContactQuery) {
    return contacts.filter(contact => {
        for (const property of Object.keys(contact) as (keyof Contact)[]) {
            // get the query object for this property
            const propertyQuery = query[property]
            // check to see if it matches
            if (propertyQuery && propertyQuery.matches(contact[property])) {
                return true
            }
        }

        return false
    })
}

const filteredContacts = searchContacts(
    [/* contacts */],
    {
        id: { matches: (id) => id === 123 },
        name: { matches: (name) => name === "Carol Weaver" },
    }
)
```

