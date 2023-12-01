---
title: "Enhancing subscription management with takeUntilDestroy in Angular"
datePublished: Fri Dec 01 2023 11:09:08 GMT+0000 (Coordinated Universal Time)
cuid: clpmiv71n000a0al380f4crnj
slug: enhancing-subscription-management-with-takeuntildestroy-in-angular
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/XFUqd0u5U7w/upload/4f9d072c4d4fa74fae07225be10295ff.jpeg
tags: development, angularjs, web-development, angular, webdev

---

Angular provides effective tools for developing robust applications, however, it is essential to manage observables subscriptions properly to prevent performance complications and potential memory leaks. This guide presents a practical approach to improve subscription management within Angular components by applying **takeUntilDestroy**.

Since Angular 16 we have a new way to unsubscribe from observables. We use an RxJS pipe called **takeUntilDestroy**. This saves us from having to manually unsubscribe in the component's OndDestry.

## **What is** takeUntilDestroy, and why is it useful?

In Angular application development, it's typical to employ observables to manage asynchronous data streams. Nonetheless, when a component is destroyed (e.g. due to a route change), appropriately disposing of subscriptions is vital to avoid memory leaks. That's where **takeUntilDestroy** comes in useful.

TakeUntilDestroy is a method that exploits an observable to decide when a subscription should be terminated. This aids in releasing resources accurately and improves our application's effectiveness.

**Recap of the old way:**

Previously, in order to unsubscribe, we had to generate a subscription and verify that the subscription was not undefined before destroying the component and activating the unsubscribe() function.

```typescript
private mySubscription: Subscription;
private mySevice = inject(myServive);

ngOnInit() {
    this.mySubscription = this.mySevice.users$
   .subscribe((users: user[]) => {
    this.users = users;
});

ngOnDestroy(): void {
  this.mySubscription?.unsubscribe();
}
```

> Note: If you are subscribed to a http subscription, it is not necessary to unsubscribe, Angular will unsubscribe itself.

**How to Use takeUntilDestroy in Angular:**

Import `DestroyRef` from `@angular/core`, we need this to know how to destroy the component.

Add a pipe to your subscription and call takeUntilDestroy with the destroyRef reference.

```typescript
private destroyRef = inject(DestroyRef);

ngOnInit() {
    this.mySubscription = this.mySevice.users$
    .pipe(takeUntilDestroy(this.destroyRef));
    .subscribe((users: user[]) => {
    this.users = users;
});
```

With these steps, your Angular component will now automatically handle unsubscribe when it is destroyed.

## Conclusion

Effective subscription management is essential in Angular to prevent performance issues and potential memory leaks. takeUntilDestroy provides a valuable tool to simplify the process, ensuring proper destruction of subscriptions when no longer required. By implementing this practice, you can increase component efficiency and deliver a smoother user experience in your Angular applications.