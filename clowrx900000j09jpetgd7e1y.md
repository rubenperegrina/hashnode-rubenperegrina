---
title: "Creating a custom RxJS operator for live search"
seoTitle: "Optimize Angular Live Search: Custom RxJS Operator"
seoDescription: "Elevate Angular performance with a custom RxJS live search operator. Enhance responsiveness, minimize redundant requests, and set smart character filters."
datePublished: Mon Nov 13 2023 10:40:40 GMT+0000 (Coordinated Universal Time)
cuid: clowrx900000j09jpetgd7e1y
slug: creating-a-custom-rxjs-operator-for-live-search
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/QoMzbNiTApY/upload/3157d09509ef771d08338073c00e0188.jpeg
tags: angularjs, web-development, angular, angular-2, frontend-development

---

## Introduction

In the dynamic landscape of Angular development, creating responsive and efficient **live search functionality** is critical. One way to achieve this is through the use of **custom RxJS operators**. In this article, we'll explore the implementation of a custom live search operator that will allow you to take your Angular applications to new heights.

## The power of custom operators

**Custom RxJS operators** allow developers to tailor their observable pipelines to specific needs. In this example, we'll focus on a **live search operator** designed for an Angular application. Let's dive into the implementation.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/rxjs-custom-operator" style="pointer-events: none"><strong>See the article code on GitHub</strong></a></div>
</div>

## Taking the requirements

Imagine that you have a search input in your application that allows you to search in your database or in a **third party API**, every search that the user does makes a cost in terms of infrastructure or the service that the third party API charges you.

One of the best practices for a search request could be to add some conditions in it, add a **debounce time** between the search of the user, if you want to give a great experience probably have a search that sends a request while the user is typing, but what happens if the user type to slow? are you prepared to send a request for every character that the user types? Of course not, with the **RxJS debounceTime operator** you can set a time between typing.

What else? maybe a good practice would be to **check the last search**, if the user is wrong and wants to do the same search again, it's not necessary to do the same request again. You can control this with the **RxJS distinctUntilChanged operator.**

Any other improvements? Yes, the last one for our live search, we want to add a **minimum of characters** to search, we don't want to search with only one or two characters, so we can use the **RxJS filter operator.**

## Creating the RxJS live search operator

With all of these things, it's easy to add some operators to our request right? but what happens if we have some searches in our application? We need to repeat this in every search? No need to.

Create the file `live-search-operator.ts`

```typescript
import { OperatorFunction, debounceTime, distinctUntilChanged, Observable, filter } from 'rxjs';
const DEFAULT_FILTER = 3;
const DEFAULT_DEBOUNCE_TIME = 300;

export function liveSearchOperator<T>(
    filterFn: (value: T) => boolean,
    debounceTimeFn: number,
    distinctFn: (value: T, otherValue: T) => boolean): OperatorFunction<T, T> {
    return (source: Observable<T>) =>
        source.pipe(
            filter(filterFn || DEFAULT_FILTER),
            debounceTime(debounceTimeFn || DEFAULT_DEBOUNCE_TIME),
            distinctUntilChanged(distinctFn)
        );
}
```

Does it! we created our **custom RxJS operator** with 3 features, we set by default **3 characters** and **300 mili seconds.**

## Implementing in our component

```typescript
import { liveSearchOperator } from './live-search-operator';
this.user$ = this.searchTerm$.pipe(
  liveSearchOperator(
    (term: string) => term.length >= 4,
    500,
    (prev, curr) => prev === curr
  ),
);
```

## Conclusion

**Custom RxJS operators** empower Angular developers to create tailored solutions for specific application needs. The **live search operator** presented here showcases how a carefully crafted operator can enhance performance and responsiveness in Angular applications. By mastering custom operators, you **unlock the potential** to build more efficient and user-friendly experiences.

In your Angular development journey, don't shy away from exploring and creating custom operators that align with your application's unique requirements. Elevate your coding prowess by harnessing the full power of **RxJS in Angular.**

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/rxjs-custom-operator" style="pointer-events: none"><strong>See the article code on GitHub</strong></a></div>
</div>