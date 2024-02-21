---
title: "Mastering inject() in Angular: A powerful resource for dependency injection"
seoTitle: "Angular Mastery: Mastering inject() for Dependency"
seoDescription: "Unlock Angular's inject() for efficient dependency injection. Enhance code clarity, simplify refactoring, and achieve conditional injection."
datePublished: Fri Nov 10 2023 07:00:09 GMT+0000 (Coordinated Universal Time)
cuid: clos9q3kh000h09k29aqxazez
slug: mastering-inject-in-angular-a-powerful-resource-for-dependency-injection
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/lPjeFCIFJwk/upload/bb60aba42dfa0b7f5410a3f82a8eb7f5.jpeg
tags: angularjs, web-development, angular, typescript, frontend-development

---

## Introduction

Dependency injection is the foundation of Angular. By using dependency injection, developers can manage a component's dependencies efficiently. In this article, we will take a deep dive into Angular's `inject()` function, which was introduced in Angular 14 and it's powerful tool for achieving **flexible** and **effective** dependency injection.

## What is inject()?

The `inject()` function is a key feature of Angular that is used to obtain instances of services or dependencies within a component or service. Allows dependency injection to be more simple and clear than other methods. Here's a simple example of how `inject()` is used:

```typescript
import { ApiService} from './api.service';
import { User } from './user.ts';
import { Component, OnInit, inject } from '@angular/core';

@Component({
  selector: 'app-example',
  template: '<p>{{ user.name }}</p>'
})
export class UserComponent implements OnInit {
  user: User;
  apiService = inject(ApiService);

  ngOnInit(): void {
    this.user = this.apiService.getUser();
  }
}
```

As you can see we don't need to inject our dependencies in the constructor, this means that we don't need to have a class to use it, we can use it in functions.

**Benefits of** `inject()`: Compared to other dependency injection methods in Angular, `inject()` offers several benefits:

* Greater code clarity.
    
* Easier refactoring and maintenance.
    
* Conditional dependency injection.
    

## Inject dependency in functions

With `inject()` we do not have to create a **resolver, guard, pipe** etc using the **CLI** and implement it in a file. It's simpler.

We can create functional guards like this:

```typescript
export function authGuard(): CanActivateFn {
  return () => {
    const oauthService: AuthService = inject(AuthService);
    if (oauthService.hasAccess() ) {
      return true;
    }
    oauthService.login();
    return false;
  };
}
```

```typescript
const routes: Route[] = [
  { path: 'home', component: HomeComponent, canActivate: [authGuard()]}
]
```

Imagine the potential of this for use in pipes, resolvers, interceptors and more!

## Conclusion

`inject()` is a powerful feature in Angular that makes dependency injection clear and flexible. Throughout this article, we've explored how to use `inject()` in components and services. Integrating inject() into your Angular development workflow can improve the readability and maintainability of your code, allowing you to build robust and easily maintainable applications. Use this tool to improve your Angular development skills and create high-quality applications.