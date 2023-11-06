---
title: "Angular module loading strategies, optimizing user experience"
seoTitle: "Angular module loading strategies, optimizing user experience"
seoDescription: "How to implement a module preloading strategy"
datePublished: Sat Nov 04 2023 12:43:40 GMT+0000 (Coordinated Universal Time)
cuid: clok1cr8h000d08jz49ecbzju
slug: angular-module-loading-strategies-optimizing-user-experience
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/jf1EomjlQi0/upload/5ac9089e14179f10c0919f8e382740c0.jpeg
tags: angularjs, web-development, typescript, frontend-development

---

When developing Angular applications, one of the key considerations is how to efficiently load and manage modules. How we handle module loading can have a significant impact on user experience and overall performance. In this post, we'll explore various module loading strategies in Angular and provide practical examples for each of them.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/angular-prefetching" style="pointer-events: none">See the article code on GitHub</a></div>
</div>

## **Lazy loading**

One of Angular's most powerful features is the ability to load modules on-demand, a concept known as `lazy loading`. This means modules are loaded only when the user needs them, which can significantly improve initial load times. Below is an example of how this is implemented in the route file `AppRoutingModule`:

```typescript
const routes: Routes = [
  {
    path: "contact",
    loadChildren: () =>
      import("./contact/contact.module").then((m) => m.ContactModule),
  },
  {
    path: "about",
    loadChildren: () =>
      import("./about/about.module").then((m) => m.AboutModule),
  },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

**StandAlone API version**

```typescript
export const routes: Routes = [
  {
    path: "contact",
    loadChildren: () =>
      import("./contact/contact.routes").then((m) => m.CONTACT_ROUTES),
  },
  {
    path: "about",
    loadChildren: () =>
      import("./about/about.routes").then((m) => m.ABOUT_ROUTES),
  },
];
```

**Directly lazy loading a standalone component**

```typescript
export const routes: Routes = [
  {
    path: "contact",
    loadComponent: () =>
      import("./contact/contact.component").then((m) => m.ContactComponent),
  },
  {
    path: "about",
    loadComponent: () =>
      import("./about/about.component").then((m) => m.AboutComponent),
  },
];
```

```typescript
bootstrapApplication(AppComponent, {
  providers: [provideRouter(routes)],
});
```

## **Preload all modules**

If you want to preload all modules in your application upfront, you can use the `PreloadAllModules` strategy. This speeds up user navigation after loading all modules at once. Here's how to enable this strategy:

```typescript
@NgModule({
  imports: [
    RouterModule.forRoot(routes, {
      preloadingStrategy: PreloadAllModules,
    }),
  ],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

**StandAlone API version**

```typescript
bootstrapApplication(AppComponent, {
  providers: [provideRouter(routes, withPreloading(PreloadAllModules))],
});
```

## **Custom module preloading**

What if you only want to preload specific modules upfront? You can create a custom preloading strategy, loading only the modules that are most crucial for the user experience. Here's an example of a custom preloading strategy:

```typescript
@Injectable({
  providedIn:'root'
})
export class PreloadingStrategyService implements PreloadingStrategy {
  private preloadedModules: string[] = [];

  preload(route: Route, load: () => Observable): Observable {
    if (route.data && route.data['preload'] && route.path) {
      this.preloadedModules.push(route.path);
      return load();
    } else {
      return of(null);
    }
  }
}
```

```typescript
const routes: Routes = [
  {
    path: "contact",
    loadChildren: () =>
      import("./contact/contact.module").then((m) => m.ContactModule),
  },
  {
    path: "about",
    loadChildren: () =>
      import("./about/about.module").then((m) => m.AboutModule),
    data: { preload: true },
  },
];

@NgModule({
  imports: [
    RouterModule.forRoot(routes, {
      preloadingStrategy: PreloadingStrategyService,
    }),
  ],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

**StandAlone API version**

```typescript
bootstrapApplication(AppComponent, {
  providers: [provideRouter(routes, withPreloading(PreloadingStrategyService))],
});
```

## **Using ngx-quicklink**

Another interesting option is the `ngx-quicklink` library, which loads modules as the links appear on the screen. This enhances user-perceived speed by loading modules in the background. To use it, you first need to install the library:

```bash
npm i ngx-quicklink
```

Then, you can enable it as follows:

```typescript
import { QuicklinkStrategy } from "ngx-quicklink";

@NgModule({
  imports: [
    RouterModule.forRoot(routes, {
      preloadingStrategy: QuicklinkStrategy,
    }),
  ],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

**StandAlone API version**

```typescript
import { quicklinkProviders, QuicklinkStrategy } from 'ngx-quicklink';

bootstrapApplication(AppComponent, {
  providers: [
    provideRouter(routes, withPreloading(QuicklinkStrategy)),
    quicklinkProviders
  ]
})
```

Import the `QuicklinkDirective` in all your standalone components that use preloading:

```typescript
import { RouterModule } from '@angular/router';
import { QuicklinkDirective } from 'ngx-quicklink';

@Component({
  standalone: true,
  imports: [RouterModule, QuicklinkDirective],
    template: `
    <a routerLink="/form">Form</a>
  `,
})
```

## **Conclusion:**

In summary, Angular offers several module loading strategies to optimize user experience and application performance. The choice of the right strategy depends on the specific needs of your project. Lazy loading, preloading, custom loading, and ngx-quicklink are powerful tools you can use to ensure your users enjoy a smooth and fast experience.

Explore these strategies and choose the one that best suits your requirements!

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/angular-prefetching" style="pointer-events: none">See the article code on GitHub</a></div>
</div>