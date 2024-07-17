---
title: "Goodbye Zone.js: What's New in Angular 18?"
seoTitle: "Angular 18: What's New Without Zone.js?"
seoDescription: "Angular 18 introduces a hybrid change detection system, reducing Zone.js dependency, enhancing performance, and adding the new Signals feature"
datePublished: Wed Jul 17 2024 16:31:40 GMT+0000 (Coordinated Universal Time)
cuid: clyq281do000409jxd97bdapc
slug: goodbye-zonejs-whats-new-in-angular-18
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/3YAIvBNlZM4/upload/66567b96945a70129a48ac7856ca33d2.jpeg
tags: tutorial, javascript, frontend, angularjs, web-development, web, angular, angular-2, webdev, typescript, frontend-development, signals

---

**Angular 18** is revolutionizing the way change detection is handled, removing the dependency on **Zone.js**. This change began in Angular 17 with the introduction of **Signals**. Now, instead of depending only on Signal components, the new hybrid detection system will automatically trigger change detection for any invoker of `markForCheck`, whether they are inside or outside of Zone.js.

### What is Zone.js?

**Zone.js** acts as a helper to check whether each component in a large application needs to be updated. Each time you use a component, **Zone.js** ensures that any change is correctly detected and updated.

### Signals: The introduction in Angular 17

**Angular 17** introduced a new concept called signals. Signals allow for more efficient interactions with components, reducing the dependency on Zone.js. Signals allow developers to handle state changes more explicitly.

### The revolution of Angular 18: Hybrid system

**Angular 18** takes this a step further with a **hybrid change detection system**. Now, any invoker of `markForCheck` will automatically trigger change detection, regardless of whether it is inside or outside of Zone.js.

Here is an example to illustrate this:

```typescript
import { Component, ChangeDetectorRef, ChangeDetectionStrategy } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: `<div>{{ mySignal }}</div>`,
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class MyComponent {
  mySignal = 'Initial Value';

  constructor(private cdr: ChangeDetectorRef) {}

  ngOnInit() {
    setTimeout(() => {
      this.mySignal = 'Updated Value';
      this.cdr.markForCheck();
    }, 3000);
  }
}
```

In this example, we manually inject `ChangeDetectorRef` and invoke `markForCheck` after updating the component's state.

### Using Signals for simplicity

With the new Signals feature in **Angular 18**, you can simplify this process:

```typescript
import { Component, ChangeDetectionStrategy } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: `{{ mySignal() }}`,
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class MyComponent {
  mySignal = signal(0);

  ngOnInit() {
    setTimeout(() => this.mySignal.set(1), 3000);
  }
}
```

In this improved version, we use a signal, and the view updates automatically without needing to manually call `markForCheck`.

### Conclusion

The main benefit of this new system is the **reduction in dependency on Zone.js**, which can improve **performance and code clarity**. However, it is important for developers to understand how Signals and the hybrid system work in order to make the most of these improvements. **Angular 18 is a revolution in change detection**, making applications more efficient and easier to maintain. Removing the dependency on Zone.js, along with the introduction of Signals and the hybrid system, is a significant step forward for Angular developers.