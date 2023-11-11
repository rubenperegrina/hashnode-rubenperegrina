---
title: "Elevating user experience: Mastering Angular 17's View Transitions API"
datePublished: Sat Nov 11 2023 07:00:09 GMT+0000 (Coordinated Universal Time)
cuid: clotp5ygc000609jwfwtxes72
slug: elevating-user-experience-mastering-angular-17s-view-transitions-api
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/NdEm7f3jq2o/upload/bdff7c54b1334ae3a0ef790b3a2f53ec.jpeg
tags: angularjs, web-development, angular, angular-2, frontend-development

---

As you know, Angular released its [new version](https://rubenperegrina.com/whats-new-in-angular-17) a few days ago, this version includes support to [view transitions API](https://rubenperegrina.com/smoother-navigation-with-angular-17s-view-transitions-api), in this article, we take a deep into an example of how can we make our application transitions between pages more smooth.

In the [last article](https://rubenperegrina.com/smoother-navigation-with-angular-17s-view-transitions-api), we saw how **view transitions API** works, but we only did a short example, now we gonna practice with a transition image between a list of sell houses to house detail.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/angular17-demo" style="pointer-events: none">See the article code on Github</a></div>
</div>

## Introduction

We want a make a transition between pages, in this pages we have a list of houses and if you click on one of them you can go to the details of this house, we want to optimize the user experience, so, we gonna make a transition in this houses images(you can see the results a few lines above).

## Configuring view transitions

First of all, we need to create a project in **Angular 17** and add the `withViewTransitions()` and `withComponentInputBinding()` in our `app.config.ts`

```typescript
import { ApplicationConfig } from '@angular/core';
import { provideRouter, withComponentInputBinding, withViewTransitions } from '@angular/router';
import { routes } from './app.routes';

export const appConfig: ApplicationConfig = {
  providers: [provideRouter(routes, withViewTransitions(), withComponentInputBinding())]
};
```

Then we need to create two pages, one for the houses list and the other one for the house details, let's create `properties.component.ts` and `property-detail.component.ts`

## Creating the routes

Once we have these two components we need to add our routes:

```typescript
export const routes: Routes = [
    {path: 'properties', component: PropertiesComponent},
    {path: 'property/:id', component: PropertyDetailComponent},
  ];
```

## Add identifiers to our JSON of houses

We will use the JSON images that [angular.dev](http://angular.dev) provides us in his tutorial but, we add a property `viewTransitionName` with the image id, this is our binding and the way Angular knows the images between two pages.

```typescript
export const properties = [
    ...
    {
      id: '9',
      name: 'Capital Safe Towns',
      city: 'Portland',
      state: 'OR',
      photo: `https://angular.dev/assets/tutorials/common/webaliser-_TPTXZd9mOo-unsplash.jpg`,
      availableUnits: 6,
      wifi: true,
      laundry: true,
    },
  ].map(property => ({...property, viewTransitionName: `view-transition-name: property-${property.id}`}));;
```

## Creating the list of houses

Now we need to render the list of houses, add the `viewTransition` and the `routerLink` to the house detail. Also, we put into practice the new Angular [control flow](https://rubenperegrina.com/how-does-angulars-new-control-flow-work) using `@for`, `@empty`, `@placeholder`, `@error` and `@loading`

```xml
  @defer(when properties) {
    <ul class="grid grid-cols-2 md:grid-cols-3 gap-3 px-4">
      @for(property of properties; track property.id) {
        <li>
          <a class="hover:scale-105 inline-block transition-all hover:contrast-125 hover:shadow-2xl"
          [routerLink]="['/property', property.id]">
          <img
          alt={{property.name}}
          class="aspect-[389/500] h-full object-cover w-full max-w-full rounded"
          [ngSrc]="property.photo"
          height="500"
          width="389"
          [style]="property.viewTransitionName"
          />
        </a>
      </li>
      } @empty {<span>No properties for sell</span>}
  </ul>
  }
  @placeholder {<span>Placeholder</span>}
  @error {<span>Error</span>}
  @loading(minimum 1s) {<span>Loading...</span>}
```

## Render the house detail

Now we only need to render the image in the `property-detail.component.ts` and bing the transition, all the work is done!

```xml
    <img
      class="aspect-[389/500] h-full object-cover w-full max-w-full rounded"
      [ngSrc]="property.photo"
      width="389"
      height="500"
      [style]="property.viewTransitionName"
    />
```

## Enjoy the results!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699458825815/3bff86b8-24d8-4bc5-bcbe-cd2fc3f32283.gif align="center")

As I said in the [last view transitions API article](https://rubenperegrina.com/smoother-navigation-with-angular-17s-view-transitions-api), we take a deep of how this magic happens in the **DOM** using the animations section of your **browser's developer tools.**

## Conclusion

As you can see the results are like magic, we **improved** a lot the **user experience** in our app by implementing the new **Angular** feature **view transitions API**.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/angular17-demo" style="pointer-events: none">See the article code on Github</a></div>
</div>

**Related articles:**

* [**Angular.dev**](http://Angular.dev) [**\- The future home for Angular Development**](https://rubenperegrina.com/angulardev-the-future-home-for-angular-development)
    
* [What's new in Angular 17?](https://rubenperegrina.com/whats-new-in-angular-17)
    
* [**How does Angular's New Control Flow work?**](https://rubenperegrina.com/how-does-angulars-new-control-flow-work)
    
* [**Smoother navigation with Angular 17's view transitions API**](https://rubenperegrina.com/smoother-navigation-with-angular-17s-view-transitions-api)