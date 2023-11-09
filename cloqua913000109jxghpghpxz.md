---
title: "Smoother navigation with Angular 17's view transitions API"
datePublished: Thu Nov 09 2023 07:00:09 GMT+0000 (Coordinated Universal Time)
cuid: cloqua913000109jxghpghpxz
slug: smoother-navigation-with-angular-17s-view-transitions-api
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/7KLa-xLbSXA/upload/c95cf7d3afbbc0d00352fd2d3f09eb6c.jpeg
tags: angularjs, web-development, angular, angular-2, frontend-development

---

One of the new features of [Angular 17](https://rubenperegrina.com/whats-new-in-angular-17) is the integration with the **View Transitions API**, this feature makes it easy to transition the DOM between pages making a nice transition for the user.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/angular-view-transitions" style="pointer-events: none"><strong>See the article code on GitHub</strong></a></div>
</div>

This feature is inside Angular Router, you can choose if you want to activate it or not, if you want to, the API activates the transition when a component is destroyed, this ensures nice transitions between pages.

It's not just to make your application look fancy, it's to provide a better user experience, you can even make your application look faster while loading some content.

## How to implement it?

You need to import `withViewTransitions` from `@angular/router`

```typescript
import { withViewTransitions } from '@angular/router';
```

Add the `withViewTransitions` function to your `provideRouter` configuration.

```typescript
bootstrapApplication(AppComponent, {
  providers: [
    provideRouter(
      routes, 
      withViewTransitions()
    ),
  ],
})
```

With this minimal setup, you can apply beautiful smooth fade-ins and fade-outs to your application.

You can see how the `::view-transition` pseudo-element applies to the **DOM**, and if you open the animations section of your **browser's developer tools**, you can debug the **view transitions API**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699358394975/ea30269d-88ff-41e9-b7c9-7026d088ea91.png align="center")

## Customizing view transitions API

If the default transitions are not enough for you, you can create your transitions to personalise your application, here are some examples of custom transitions:

```css
@keyframes fade-in {
  from {
    opacity: 0;
  }
}

@keyframes fade-out {
  to {
    opacity: 0;
  }
}

@keyframes slide-from-right {
  from {
    transform: translateX(30px);
  }
}

@keyframes slide-to-left {
  to {
    transform: translateX(-30px);
  }
}
```

In the next view transitions articles we will implement some cool custom transitions and explore all the benefits, this is just a first look at the feature.

## Conclusion

This is a game changer for Angular, we're jumping into the new wave of applications that use the view transitions API, it's much easier for developers to implement and improves the user experience a lot, this is just the beginning, we still need to do more research on how we can further optimise our applications and make them render faster.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/angular-view-transitions" style="pointer-events: none"><strong>See the article code on GitHub</strong></a></div>
</div>

**Related articles:**

* [Angular.dev - The future home for Angular Development](https://rubenperegrina.com/angulardev-the-future-home-for-angular-development)
    
* [What's new in Angular 17?](https://rubenperegrina.com/whats-new-in-angular-17)
    
* [How does Angular's New Control Flow work?](https://rubenperegrina.com/how-does-angulars-new-control-flow-work)