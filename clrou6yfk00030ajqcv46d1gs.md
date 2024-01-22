---
title: "Angular Roadmap - The guide I wanted to have before starting in Angular"
datePublished: Mon Jan 22 2024 11:21:10 GMT+0000 (Coordinated Universal Time)
cuid: clrou6yfk00030ajqcv46d1gs
slug: angular-roadmap-the-guide-i-wanted-to-have-before-starting-in-angular
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/vv-oEGlN-4E/upload/32c238abaf9798060fb05315493e94e8.jpeg
tags: tutorial, javascript, frontend, development, angularjs, angular, developer, typescript, guide, frontend-development, front-end-cik5w32oi016zos53hitiymhh

---

## Introduction

As a beginner, it's easy to feel overwhelmed when diving into a new framework like Angular, but fear not, we're here to guide you! In this post, we'll break down a step-by-step roadmap that I wish I had when I started my Angular programming journey. Keep reading to discover essential tips, tricks, and guides that will set you apart in the world of Angular development.

**Prerequisites:** Before we dive into Angular, it's essential to ensure you have a solid foundation in JavaScript. If you're not familiar with JavaScript basics, take some time to acquaint yourself with the fundamentals.

**Understanding Angular:** Angular, as a robust web application framework, supports full-stack development. Its architecture is centred around **TypeScript** and the concept of components, which are fundamental to creating reactive single-page applications **(SPAs)**. Understanding these components and how they interact is key to mastering Angular.

By following these steps, you'll build a strong foundation in both TypeScript and Angular, setting the stage for a successful journey into the dynamic world of web development.

> Before starting, I gathered all the useful documentation links that I found and recommend checking them out.

## Learn TypeScript basics

Angular is constructed with TypeScript, a strongly typed, object-oriented, and compiled programming language that extends JavaScript. To navigate the world of Angular effectively, it's crucial to grasp the basics of TypeScript. This statically typed superset of JavaScript not only enhances code reliability and maintainability but is also the backbone of Angular development.

* [Structural Typing](https://www.typescriptlang.org/docs/handbook/type-compatibility.html)
    
* [Type Interface](https://www.typescriptlang.org/docs/handbook/type-inference.html)
    
* [Union Types](https://www.typescriptlang.org/docs/handbook/unions-and-intersections.html)
    
* [Built-in Types](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes-func.html#built-in-types)
    
* [Type Guards](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes-func.html#built-in-types)
    
* [Generics](https://www.typescriptlang.org/docs/handbook/2/generics.html#handbook-content)
    
* [Decorators](https://www.typescriptlang.org/docs/handbook/decorators.html#handbook-content)
    
* [Utility Types](https://rubenperegrina.com/exploring-the-essentials-typescript-utility-types)
    

> [TypeScript playground](https://www.typescriptlang.org/play?#code/PTAEHUFMBsGMHsC2lQBd5oBYoCoE8AHSAZVgCcBLA1UABWgEM8BzM+AVwDsATAGiwoBnUENANQAd0gAjQRVSQAUCEmYKsTKGYUAbpGF4OY0BoadYKdJMoL+gzAzIoz3UNEiPOofEVKVqAHSKymAAmkYI7NCuqGqcANag8ABmIjQUXrFOKBJMggBcISGgoAC0oACCbvCwDKgU8JkY7p7ehCTkVDQS2E6gnPCxGcwmZqDSTgzxxWWVoASMFmgYkAAeRJTInN3ymj4d-jSCeNsMq-wuoPaOltigAKoASgAywhK7SbGQZIIz5VWCFzSeCrZagNYbChbHaxUDcCjJZLfSDbExIAgUdxkUBIursJzCFJtXydajBBCcQQ0MwAUVWDEQC0gADVHBQGNJ3KAALygABEAAkYNAMOB4GRonzFBTBPB3AERcwABS0+mM9ysygc9wASmCKhwzQ8ZC8iHFzmB7BoXzcZmY7AYzEg-Fg0HUiQ58D0Ii8fLpDKZgj5SWxfPADlQAHJhAA5SASPlBFQAeS+ZHegmdWkgR1QjgUrmkeFATjNOmGWH0KAQiGhwkuNok4uiIgMHGxCyYrA4PCCJSAA) for practice

## Learn Angular CLI

The [Angular CLI](https://angular.dev/tools/cli), a command-line interface tool, streamlines the initiation, development, scaffolding, and maintenance of Angular applications directly from a command shell. To install the latest [Angular CLI](https://angular.dev/tools/cli), execute the following command:

```bash
npm install -g @angular/cli
```

Create a new project:

```bash
ng new my-app
```

One of the common commands if you need help:

```bash
ng --help
ng generate --help
ng build --help
```

Quick guide for generating components in Angular:

| Command | Description |
| --- | --- |
| ng g component \[name\] ng g c \[name\] | Create a new component, you can put the route also, \[/path/name\] |
| ng g directive \[name\] ng g d \[name\] | Create a new directive. |
| ng g guard \[name\] ng g g \[name\] | Create a new guard for routes protecting. |
| ng g interceptor \[name\] | Create a new interceptor. |
| ng g module \[name\] ng g m \[name\] | Create a new module, you can aggregate components inside. |
| ng g pipe \[name\] ng g p \[name\] | Create a new pipe, a data transformer. |
| ng g service \[name\] ng g s \[name\] | Create a new service, that permits sharing information in the application and making HTTP calls. |

Also, you can add flags at the ends of the command to add features, here are some examples:

| **Flag** | **Description** |
| --- | --- |
| ng g c --help | Show the whole help for that command |
| ng g c \[name\] --dry-run | Run the command without changing files. Useful if you are not sure what the command will do |
| ng g c \[name\] --flat | Creates the new files at the specified level without creating a new new directory. |
| ng g c \[name\] --inline-style ng g c \[name\] -s | Include the styles in the same container file (.ts) |

> I recommend learning [Angular file structure](https://angular.dev/reference/configs/file-structure#library-project-files): How the components are organized like in modules, and their components, services, etc.

## Lifecycle Hooks

A [component's lifecycle](https://angular.dev/guide/components/lifecycle) in Angular begins when the component class is instantiated and the view, along with its child views, is rendered. This lifecycle includes change detection, where Angular monitors changes in data-bound properties, updating both the view and the component instance. The [lifecycle](https://angular.dev/guide/components/lifecycle) concludes when Angular destroys the component instance, removing its template from the DOM. Similar to components, directives follow a lifecycle involving creation, updates, and destruction during execution.

To interact with these lifecycles, your application can utilize [lifecycle hook](https://angular.dev/guide/components/lifecycle) methods, which allow you to handle key events such as initialization, change detection, response to updates, and cleanup before deletion. The essential [Angular lifecycle hooks](https://angular.dev/guide/components/lifecycle) are:

| **OnChanges** | Called when the input properties have changed |
| --- | --- |
| [**OnInit**](https://angular.dev/guide/components/lifecycle#ngoninit) | Called on initialization |
| [**DoCheck**](https://angular.dev/guide/components/lifecycle#ngdocheck) | Developer’s custom change detection |
| [**OnDestroy**](https://angular.dev/guide/components/lifecycle#ngondestroy) | Called before the component is destroyed |
| [**AfterContentInit**](https://angular.dev/guide/components/lifecycle#ngaftercontentinit) | Called when the component’s content `ngContent` is initialized |
| [**AfterContentChecked**](https://angular.dev/guide/components/lifecycle#ngaftercontentchecked) | Called when the component’s content is updated or checked for updates |
| [**AfterViewInit**](https://angular.dev/guide/components/lifecycle#ngafterviewinit) | Called when the component’s projected view has been initialized |
| [**AfterViewChecked**](https://angular.dev/guide/components/lifecycle#ngafterviewchecked) | Called after the projected view has been checked |

> See more about the Angular's lifecycle hooks [here](https://angular.dev/guide/components/lifecycle)

## Templates

A component, comprising a TypeScript class, an HTML template, and a CSS style sheet, governs a designated area of the screen known as a view. The TypeScript class orchestrates the interaction between the [HTML template](https://angular.dev/guide/templates) and the resulting DOM structure, while the style sheet dictates the component's appearance.

In an Angular application, distinct components are employed to define and manage various facets of the application, there are a few things that you need to know before continuing:

* **Interpolation**: Involves [embedding expressions](https://angular.dev/guide/templates/interpolation) into marked-up text using double curly braces {{ }} as delimiters. Angular then substitutes `currentCustomer` with the string value of the corresponding component property.
    
* **Property binding**: Enables the assignment of values to properties of HTML elements or directives. By [enclosing the element's property in square brackets](https://angular.dev/guide/templates/property-binding) \[\], Angular interprets the right-hand side of the assignment as a dynamic expression.
    
* **Template statements:** Are employed in HTML to respond to user events, facilitating actions like [displaying dynamic content](https://angular.dev/guide/templates/template-statements) or submitting forms. By enclosing the event in (), Angular evaluates the right-hand side of the assignment as one or more template statements linked together with semicolons (;).
    
* **Binding(data, props, attrs, events):** In Angular templates, [bindings](https://angular.dev/guide/templates/binding) establish a dynamic link between the view and the model, ensuring synchronization.
    
    * [**Property Binding**](https://angular.dev/guide/templates/property-binding)**:** Sets values for properties of HTML elements or directives.
        
    * [**Attribute Binding**](https://angular.dev/guide/templates/attribute-binding)**:** Directly sets values for attributes of HTML elements.
        
    * [**Event Binding**](https://angular.dev/guide/templates/event-binding)**:** Listens for and responds to user actions, like keystrokes, mouse movements, clicks, and touches.
        
    * [**Two-Way Data Binding**](https://angular.dev/guide/templates/two-way-binding)**:** Combines property and event binding, facilitating data sharing between components.
        
* [**Reference variables**](https://angular.dev/guide/templates/reference-variables)**:** Enable the utilization of data from one section of a template in another. These variables can reference a DOM element within a template, component, or directive. To declare a template reference variable, employ the hash symbol, #, in the template.
    
* [@Input() @Output()](https://angular.dev/guide/templates/two-way-binding): facilitate communication between a child and its parent component in Angular. With `@Input()`, a parent component can update data in the child component, while `@Output()` allows the child to send data to the parent component.
    

Some examples:

```xml
// Render the title propertu
<p>{{ title }}</p>
// Render the image with the url property
<img alt="item" src="{{ itemImageUrl }}">
// Call deleteHero function when click button
<button type="button" (click)="deleteHero()">Delete hero</button>
// Call the function onSubmit with form parameteres
<form #heroForm (ngSubmit)="onSubmit(heroForm)"> ... </form>
// Disabled o enabled button by condition isUnchanged
<button type="button" [disabled]="isUnchanged">Disabled Button</button>
// Shareing data between child and parent component
<app-item-detail [childItem]="parentItem"></app-item-detail>
// Two way data binding between child and parent component
<app-sizer [(size)]="fontSizePx"></app-sizer>
```

> Take it easy to understand all of the concepts, I know the first impression could be difficult. [This documentation maybe could be useful](https://angular.dev/guide/templates)

## Routing

[Angular's routing](https://angular.dev/guide/routing) empowers users to construct a single-page application featuring multiple views and seamless navigation between them. This enables users to switch between views without sacrificing the application state and properties.

Here is a short example of how can [configure routes](https://angular.dev/guide/routing/router-reference):

```typescript
const routes: Routes = [
    { path: 'home', component: HomeComponent },
    { path: 'detail/:id', component: ... },
    { path: 'about', component: ... },
    { path: 'items', // lazy load a module
    loadChildren: () => import('./items/
    items.module').then(m => m.ItemsModule)}
]);
```

We need to put the [router-outlet](https://angular.dev/guide/routing/router-reference) element in the HTML to say Angular where we want to render our routes:

```xml
<router-outlet></router-outlet>
```

We use the control navidation to [link our routes](https://angular.dev/guide/routing/router-reference) inside of our app like this:

```xml
<a routerLink="/home">
<a [routerLink]="[ '/detail', user.id]”>
```

# Learn the basics of RxJS

[RxJS](https://rxjs.dev/) is a reactive library used to implement reactive programming to deal with async implementation, callbacks, and event-based programs.

* [**Observer Pattern**](https://rxjs.dev/api/index/interface/Observer): The observer pattern is a software design approach where a subject object keeps a list of dependents (observers) and automatically informs them of any state changes by calling one of their methods. In Angular, this pattern is employed through Observables, where objects subscribe to them using the `subscribe` method and respond when the observable undergoes any relevant action.
    
* [**Observable lifecycle**](https://rxjs.dev/api/index/interface/Observer)**:** An observable, functioning as a wrapper for a data stream, enables message passing within your application. However, it becomes meaningful only when an observer subscribes to it. The observer, consuming data emitted by the observable, continues to receive values until either the observable completes or the observer unsubscribes. This asynchronous process allows for diverse operations like updating the user interface or handling JSON responses.
    
    The observable life cycle consists of four stages: creation, subscription, execution, and destruction.
    
* [**RxJS vs Promises**](https://rxjs.dev/deprecations/to-promise)**:** Eager vs. Lazy, Asynchronous Nature, Data Delivery.
    

# Learn how to use RxJS operators

**RxJS** is primarily valued for its [operators](https://rxjs.dev/guide/operators), which, while built on the foundation of Observables, play a pivotal role. These [operators](https://rxjs.dev/guide/operators) serve as crucial components, enabling the seamless composition of intricate asynchronous code in a declarative fashion.

**There are two kinds of operators:**

**Pipeable Operators**, like `filter(…)` and `mergeMap(…)`, can be applied to **Observables** using the syntax `observableInstance.pipe(operator())`. These operators do **not alter the existing Observable** instance; instead, they **create a new Observable**. Subscribing to the new **Observable** also subscribes to the original one.

Piping involves chaining these operators together, enhancing readability. The `.pipe()` method of **Observables** achieves this concisely:

```typescript
codeobs.pipe(op1(), op2(), op3(), op4());
```

**Creation Operators** are standalone functions used to **create new Observables** with predefined behaviors or by **combining other Observables**. For example, the interval function takes a number as an input argument and produces an Observable:

```typescript
const observable = interval(1000);
```

These operators are distinct from pipeable operators and will be explored in more detail in a later section.

## Are there more?

Yes, this is only the basics, with this you are ready to create your first Angular application, create some components, link to a routes and render some information, but this is just the beginning, Angular has a lot more, here are a few more concepts that you need to know to take all the Angular advantages:

* [**Forms**](https://angular.dev/guide/forms)
    
* [**Pipes**](https://angular.dev/guide/pipes)
    
* [**Directives**](https://angular.dev/guide/directives)
    
* [**Guards**](https://angular.dev/api/router/CanActivate)
    
* [**Interceptors**](https://angular.dev/guide/http/interceptors#configuring-interceptors)
    
* [**Resolvers**](https://angular.dev/api/router/Resolve#)
    
* [**HttpClient**](https://angular.dev/api/common/http/HttpClient)
    
* [Testing](https://angular.dev/guide/testing)
    
* [Signals](https://angular.dev/guide/signals)
    
* [Deferrable Views](https://angular.dev/guide/defer)
    

## Conclusion

Maybe from the outside Angular looks like another framework, but in my opinion, it's not it. Angular it's a platform more than a framework, it's a platform that offers you all the necessary things to build great quality applications, most of the time you don't need to install third-party libraries to do some things, Angular has many features like SRR, PWA, great forms, good security etc.

Many themes have remained to talk about in this article, maybe I can write another article with more foundation, let me know in the comments.

## Information that may interest you

* [https://rubenperegrina.com/series/angular](https://rubenperegrina.com/series/angular)
    
* [https://angular.io/docs](https://angular.io/docs)
    
* [https://angular.dev/overview](https://angular.dev/overview)
    
* [https://angular.dev/tutorials/learn-angular](https://angular.dev/tutorials/learn-angular)
    
* [https://angular.dev/tutorials/first-app](https://angular.dev/tutorials/first-app)
    
* [https://roadmap.sh/angular](https://roadmap.sh/angular)