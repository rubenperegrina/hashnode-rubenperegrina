---
title: "5 Angular best practices for robust development"
datePublished: Fri Dec 08 2023 19:22:31 GMT+0000 (Coordinated Universal Time)
cuid: clpx0kn8z000008iecvyi2ox8
slug: 5-angular-best-practices-for-robust-development
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/hbnH0ILjUZE/upload/d2a129d3874064e4d8392c50eb76a0a9.jpeg
tags: performance, angularjs, web-development, angular, best-practices

---

**Angular** is a robust framework developed by **Google** that allows developers to build dynamic single page applications based on TypeScript. As we delve into the intricate world of Angular development, it's crucial to navigate with precision and expertise. In this article, we'll explore **five advanced strategies** that go beyond the basics and unlock the full potential of Angular for seamless and superior development.

## Increase efficiency with Angular CLI

* Angular CLI is essential for project **creation and management**
    
* It provides a standardized, efficient way to bootstrap, develop, test, and deploy Angular applications.
    

Here are a few examples:

```bash
# Generate a new service
ng generate service my-service
# Run unit tests
ng test
# Build the application for production
ng build --prod
# Add a dependency (e.g., Angular Material)
ng add @angular/material
# Update Angular CLI to the latest version
ng update @angular/cli
# Add Angular Routing to the project
ng generate module app-routing --flat --module=app
# Serve the application on a different port
ng serve --port 4201
# Create a production build with AOT compilation
ng build --prod --aot
# Run end-to-end (e2e) tests
ng e2e
```

## Build maintainable code by aplying single responsibility principle

* Each component, service, or module should have a **single responsibility**
    
* The single responsibility principle promotes **maintainability, readability, and reusability**, ensuring an understandable and debuggable code base.
    

```typescript
import { Component, Input } from '@angular/core';
@Component({
  selector: 'app-user',
  template: `
    <div>
      <h2>User Details</h2>
      <p>Name: {{ user.name }}</p>
      <p>Email: {{ user.email }}</p>
    </div>
  `,
})
export class UserComponent {
  @Input() user: UserInfo;
}
export interface UserInfo {
  name: string;
  email: string;
}
```

## Improve the performance with OnPush change detection

* Use **ChangeDetectionStrategy.OnPush** to optimize component change detection.
    
* OnPush reduces the number of checks, significantly improving performance, especially in larger applications.
    

```typescript
import { Component, ChangeDetectionStrategy } from '@angular/core';
@Component({
  selector: 'app-user',
  template: '<div>{{ user.name }}</div>',
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class UserComponent {
  user = { name: 'Rubén Peregrina' };
}
```

## Implement Smart Component Architecture

* Use an intelligent component architecture for **improved maintainability** and scalability.
    
* This architecture **improves code organization**, making it easier to understand and debug.
    

```typescript
import { Component } from '@angular/core';
@Component({
  selector: 'app-user-container',
  template: `
    <h2>User Management</h2>
    <app-user-details [selectedUser]="selectedUser"></app-user-details>
  `,
})
export class UserContainerComponent{
  selectedUser: User = [name: 'Rubén', email: 'ruben@hashnode.com'];
}
```

```typescript
import { Component, Input } from '@angular/core';
@Component({
  selector: 'app-user-details',
  template: `
    @if (selectedUser){
      <h3>User Details</h3>
      <p>Name: {{ selectedUser.name }}</p>
      <p>Email: {{ selectedUser.email }}</p>
    }
  `,
})
export class UserDetailsComponent {
  @Input() selectedUser: UserInfo;
}
```

## Lazy loading for improved performance

* Implement lazy loading for feature modules to load them on demand.
    
* Lazy loading **reduces the initial bundle size** and speeds up the initial load time of the application.
    

```typescript
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
const routes: Routes = [
  {
    path: 'dashboard',
    loadChildren: () => import('./dashboard/dashboard.module')
    .then(m => m.DashboardModule),
  },
];
@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

## Conclusion

Here are some examples of how can you optimize and improve your Angular application, you can increase your **Lighthouse** stats by applying these examples.