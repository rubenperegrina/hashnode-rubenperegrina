---
title: "Exploring the essentials TypeScript utility types"
datePublished: Sat Nov 04 2023 13:14:34 GMT+0000 (Coordinated Universal Time)
cuid: clok2ghi9000208icb6puhjz1
slug: exploring-the-essentials-typescript-utility-types
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/9vQG6v1md1s/upload/527401bbc8b8c5aec503f47bea0adb69.jpeg
tags: typescript

---

TypeScript is a strongly typed superset of JavaScript that adds static typing to the language. One of the powerful features of TypeScript is its utility types. Utility types are predefined types that help in manipulating and transforming other types. We will explore some commonly used utility types in TypeScript and provide code examples to demonstrate their usage.

## **Partial**

The `Partial` utility type provide a convenient way to make all properties of a type optional. Let's consider an example where we have a `Person` type with two properties: `name` and `age`. By using `Partial<Person>`, we can create a new type where both properties become optional. This allows us to define objects with only some properties filled in.

```typescript
type Person = {
    name: string;
    age: number;
};

type PartialPerson = Partial<Person>;
// { name?: string; age?: number; }
```

## **Required**

On the other hand, `Required` make all properties required. `Required<Person>` makes both properties mandatory, ensuring that all objects of this type have both properties defined.

```typescript
type Person = {
    name: string;
    age: number;
};

type RequiredPerson = Required<Person>;
// { name: string; age: number; }
```

## **Readonly**

The `Readonly` utility type is used to create a new type where all properties are readonly, meaning they cannot be modified after initialization. This is especially useful when working with immutable data structures or when you want to prevent accidental modifications to certain objects.

```typescript
type Point = {
  x: number;
  y: number;
};

type ReadonlyPoint = Readonly<Point>;
// { readonly x: number; readonly y: number; 
```

## **Pick**

The `Pick` utility type allow you to select specific properties from a given type. Pick takes a type and a list of property names as arguments and returns a new type with only those properties.

```typescript
type User = {
    name: string;
    city: string;
    active: boolean;
    role: string[];
    age: number;
}

type UserName = Pick<User, 'name'>;
// { name: string; } 
```

## **Omit**

Conversely, `Omit` exclude specific properties from a given type, takes a type and a list of property names to exclude and returns a new type without those properties.

```typescript
type User = {
    name: string;
    city: string;
    age: number;
}

type UserWithoutAge = Omit<User, 'age'>;
// { name: string; city: string; }
```

## **Record**

The `Record` utility type is used to create an object type with specified keys and a shared value type. This is particularly useful when you want to define a dictionary or a map with a specific set of keys and a common value type.

```typescript
type Fruit = 'apple' | 'banana' | 'orange';
type FruitInventory = Record<Fruit, number>;

const fruitCounts: FruitInventory = {
  apple: 10,
  banana: 5,
  orange: 8,
};
```

## **Conclusion:**

TypeScript's utility types provide powerful tools for manipulating and transforming types. We explored some commonly used utility types, including `Partial`, `Required`, `Readonly`, `Pick`, `Omit`, and `Record`. By leveraging these utility types, you can write more expressive and safer code in TypeScript. Start using these utility types in your projects and unlock the full potential of TypeScript.