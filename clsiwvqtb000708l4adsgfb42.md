---
title: "How to use environments in Angular"
datePublished: Mon Feb 12 2024 12:29:31 GMT+0000 (Coordinated Universal Time)
cuid: clsiwvqtb000708l4adsgfb42
slug: how-to-use-environments-in-angular
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/auEPahZjT40/upload/026d204e0c57767161470ce66dc25690.jpeg
tags: tutorial, frontend, development, angularjs, web-development, angular, angular-2, webdev, developer, typescript, frontend-development

---

Creating and managing environments in Angular applications could be difficult, especially if we have a lot of them and you never work with them.

In this article, we will take a look at how Angular applications manage this and we will create a few examples to learn it. But, before we dive into that, let's cover some basics.

## What is an environment?

An environment is a configuration that you can make to work with different scenarios in your application, imagine that you are developing an application and you need to have dev, test and staging environments to deal with your data base or API.

When you run a builder target, such as build, serve, and test, Angular replaces the environment default file for the one you selected.

> Since Angular 14 we don't have the environments folder by default when we create a new project, we need to create it with: `ng generate environments`

## How can I create it?

Once we have our environments folder created in *src/environments*, we have a default configuration environment `environment.ts`

This file provides us the default configuration for production, we can add different ones like staging, development.

```typescript
my-app/src/environments
├── environment.development.ts
├── environment.staging.ts
└── environment.ts
```

The base file contains the default configuration like this:

```typescript
export const environment = {
  production: true
};
```

The build targets use this file as a default if we do not specify one.

Now we can add more values to the environment like the APIs, and URLs that we need to use:

```typescript
export const environment = {
  production: true,
  apiUrl: 'http://my-prod-url'
};
```

> Always check that we have our environments configurates in angular.json file like this:

```typescript
"configurations": {
    "development": {
      "fileReplacements": [
          {
            "replace": "src/environments/environment.ts",
            "with": "src/environments/environment.development.ts"
          }
        ],
        ...
```

## Using specific environments in our app

Now it's the time to use our environment values in the components and services.

To ensure the build, serve and test commands use the correct file, we have to use the original environment file.

We just to import the file into our component or service like this:

```typescript
import { environment } from './environments/environment';
```

Then we can access to values that we defined before.

## Build, serve and test with a specific environment

Once we create our environment, add some values, and use these values in our components it's time to select which environment we want to use for build, serve or test our application.

Here there are a few examples:

```typescript
ng build --configuration development
ng serve --configuration development
ng test --configuration development
```

With this commands, Angular replaces the s*rc/environments/environment.ts* file with the development specific one.

We can do the same for other environments like staging production etc.

## Conclusion

Now we have more knowledge about how Angular manages the environments in our applications, and with this we can develop more complex and security applications.