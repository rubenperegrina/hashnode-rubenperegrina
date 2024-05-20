---
title: "Most common RxJs operators used in Angular"
seoTitle: "Top RxJs Operators in Angular"
seoDescription: "Learn about the most common RxJs operators used in Angular with examples and visual diagrams"
datePublished: Mon May 20 2024 17:56:56 GMT+0000 (Coordinated Universal Time)
cuid: clwf9qa4u00040al8blkkcfom
slug: most-common-rxjs-operators-used-in-angular
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/ImcUkZ72oUs/upload/825b77968b690c16475fc37bebb63878.jpeg
tags: reactive-programming, javascript, frontend, asynchronous, angularjs, web-development, angular, angular-2, webdev, typescript, rxjs, frontend-development

---

RxJs is a fundamental part of Angular, although signals have been implemented since version 16, and it is expected that [RxJs](https://rxjs.dev/) will be used less and less. For now, there are many projects using it, and it will be around for a while.

It is important to understand how it works and what its main advantages are. It's a powerful library for **handling asynchronous operations**, but there are many operators, and sometimes it's hard to understand what each one is for and which one is best to use at any given time. This article aims to explain with examples which ones are **most commonly used**.

> An operator is a function used in an observable that controls and emits only the information we are interested in, in the way we need it.

## map

It is one of the most common operators in RxJs, and you have probably seen it many times. `map` allows us to transform the data emitted by the observable without altering it. Let's have a look at an example:

```typescript
const number$ = range(1, 5);

number$.pipe(map((number) => number * 2)).subscribe(console.log);
// output: 2, 4, 6, 8, 10
```

As we can see, the expected output would be `1, 2, 3, 4, 5`, but by applying map, we transform the values of the observable, in this case multiplying the values by two.

Here is a more visual example from the [official RxJs documentation](https://rxjs.dev/api/operators/map) where the arrow above is the initial data stream of the observable and the one below is after applying map.

![A diagram showing a mapping function. The top row has circles with numbers 1, 2, and 3. The middle row shows the function "map(x => 10 * x)". The bottom row has circles with numbers 10, 20, and 30, indicating the result of applying the function to the numbers in the top row.](https://rxjs.dev/assets/images/marble-diagrams/map.png align="left")

## filter

The filter operator is used to filter the values of the observable stream. With this operator, we only emit those values that march the condition we set. Let's look at an example.

```typescript
const number$ = range(1, 10);

number$.pipe(filter((n) => n > 5)).subscribe(console.log);
// output: 6, 7, 8, 9, 10
```

In this way, we filter the values of the observable and return only those that match the condition. Without the filter, the output would be `1, 2, 3, 4, 5...`. After applying the filter, only values greater than 5 are returned. Let's look at a visual example:

![A diagram showing a sequence of numbers (0, 1, 2, 3, 4) being filtered through a function "filter(x => x % 2 === 1)", resulting in a new sequence of odd numbers (1, 3).](https://rxjs.dev/assets/images/marble-diagrams/filter.png align="left")

## tap

It is a utility operator that allows performing side actions that do not affect the main flow without affecting the emission or transformation of the observable.

It is a useful operator for debugging and testing the observable without modifying the output. Any logic we put inside the tap will help us debug and test, but the data stream remains intact. Let's look at an example:

```typescript
of(Math.random()).pipe(
  tap(console.log),
  map(n => n > 0.5 ? 'big' : 'small')
).subscribe(console.log);
```

In this example with the map operator, we filter the numbers received from the observable to log "big" or "small" to the console depending on whether they are greater or less than 0.5. This is fine, but for development reasons, we want to know what number was initially received before filtering. By adding the tap, we can find out what it was. Let's look at a visual example from the [official documentation](https://rxjs.dev/api/index/function/tap):

![Diagram showing the use of the `tap` operator in RxJS. The top line has three colored circles labeled 1, 2, and 3. The middle box contains the code `tap(x => console.log(x))`. The bottom line shows the same three colored circles with a blue outline, indicating the values are logged but unchanged.](https://rxjs.dev/assets/images/marble-diagrams/tap.png align="left")

## take

The take operator emits the first n values and then completes the observable. The argument `count` specifies the number of values the observable should emit before completing. If the observable emits fewer values than the specified maximum, it will simply emit those and complete, regardless of whether the source has completed or not.

```typescript
const intervalCount = interval(1000);
const takeFive = intervalCount.pipe(take(5));
takeFive.subscribe(x => console.log(x));
 
// output:
// 0
// 1
// 2
// 3
// 4
```

In this example, using the interval operator, it should emit a value every second, but by adding the take operator with a count of 5, it only emits 5 values and then completes. The take operator can also be used together with others such as filter, map, and mergeMap to manipulate and control the values emitted by an observable. Let's have a look at a visual example from the [official documentation](https://rxjs.dev/api/index/function/take):

![A diagram showing the "take(2)" operation on a sequence of elements. The original sequence contains elements "a", "b", "c", and "d". After applying the "take(2)" operation, the resulting sequence contains only the first two elements: "a" and "b".](https://rxjs.dev/assets/images/marble-diagrams/take.png align="left")

## Conclusion

These are just some of the most commonly used RxJs operators, but there are many more. Understanding how they work can be very useful, especially when working on Angular applications. These operators make data handling easier and save us a lot of time. However, RxJs has a high learning curve; the first time you use it can be a bit overwhelming. That's why it's important to learn the basics well from the start. We will look at more operators in the following articles.

**Other RxJs articles you may be interested in:**

* [Handling errors in Angular with the retry operator](https://rubenperegrina.com/handling-errors-in-angular-with-retry-operator)
    
* [Creating a custom RxJs operator for live search](https://rubenperegrina.com/creating-a-custom-rxjs-operator-for-live-search)
    
* [Enhancing subscription management with takeUntilDestroy in Angular](https://rubenperegrina.com/enhancing-subscription-management-with-takeuntildestroy-in-angular)