---
title: "Exploring Angular 17.1's revolutionary feature: Input Signals"
datePublished: Thu Feb 01 2024 09:41:09 GMT+0000 (Coordinated Universal Time)
cuid: cls310uu1000f0al50s3naaw2
slug: exploring-angular-171s-revolutionary-feature-input-signals
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/yjygDnvRuaI/upload/24677aae283c1c3040b0ba5ca83c025c.jpeg
tags: tutorial, javascript, development, angularjs, web-development, angular, angular-2, webdev, developer, typescript

---

**Angular 17.1** has recently unveiled a groundbreaking feature – **Input Signals**. This latest addition transforms the way we handle component inputs, replacing the familiar **@Input decorator** with a powerful function called input(). In this article, we'll explore the benefits of Signal Inputs, their three distinct flavors, and how they bring a new level of flexibility and reactivity to Angular components.

Angular 17.1 introduces Input Signals as a developer preview, offering developers an alternative to the traditional @Input decorator. Signal Inputs provide a new approach to handling component input values, allowing for increased flexibility and reactivity.

The primary syntax shift comes with the introduction of the input() function from @angular/core, which creates input values received as signals. Let's look at the three available flavours of signal inputs:

## Default value Signal:

Resolves to a Signal of a specific type.

```typescript
export class SampleComponent {
  name = input<string>('Angular');
}
```

The **'name'** signal can be accessed directly, enabling dynamic updates without the need for `ngOnInit` or `ngOnChanges`.

## Optional value Signal:

Requires a generic type and results in a union type containing undefined.

```typescript
export class OptionalComponent {
  value = input<number>(); // number | undefined
}
```

This allows for optional inputs, accommodating scenarios where the value may or may not be present.

## Required value Signal:

Expects a generic type but does not include undefined in the union type.

```typescript
export class RequiredComponent {
  firstName = input<string>(); // string | undefined
  lastName = input.required<string>(); // string
}
```

The **'lastName'** signal ensures that a value is provided, throwing a runtime error if accessed before initialization.

> In addition, Angular 17.1 supports transformation functions for type mapping and parameter binding from the router, increasing the versatility of signal inputs.

## Conclusion

Angular 17.1's Signal Inputs mark a significant evolution in the way we handle component inputs. Using the input() function, developers can embrace a more reactive and flexible approach to managing input values. The three flavors – default, optional, and required – cater to a variety of use cases, providing a seamless transition from the traditional @Input decorator. As Angular continues to innovate, Signal Inputs open up new possibilities for cleaner, more dynamic component architectures.