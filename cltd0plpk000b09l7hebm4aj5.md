---
title: "What type of builders there are in Angular?"
datePublished: Mon Mar 04 2024 14:09:48 GMT+0000 (Coordinated Universal Time)
cuid: cltd0plpk000b09l7hebm4aj5
slug: what-type-of-builders-there-are-in-angular
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/sTw2KYpoujk/upload/3984113f3b35e01d12fc24d2f0ff60cb.jpeg
tags: tutorial, javascript, frontend, angularjs, web-development, web, angular, angular-2, webdev, typescript, frontend-development, front-end-cik5w32oi016zos53hitiymhh, ssr, vite, esbuild

---

Since the release of Angular 17, now we have three different builders to choose from when building our applications. These builders are based on **Webpack**, **EsBuild**, and serve the purpose of **Server-Side Rendering (SSR)**. In this article, we will explore the differences between them and answer the common question: **which is better and when should you use each?** We will start by exploring these builders.

## Introduction

Developers must carefully consider the builder when creating a robust Angular application, as this choice significantly impacts performance and development efficiency. Angular 17 introduces three different builders, and this article will focus on a comprehensive overview to help developers make the right decisions.

## Builders overview:

When you go to the [new Angular website](https://angular.dev/tools/cli/build#) and exploring the available builders, you will come across three main types, excluding the fourth, which is dedicated to libraries. Let's look at each of them:

**@angular-devkit/build-angular:browser (Webpack-Based):**

This is the oldest and most commonly used builder, provide bundling client-side applications for browser use with Webpack. It provides a **smooth transition to new Angular features**, particularly if there are dependencies or customizations in Webpack.

**@angular-devkit/build-angular:browser-esbuild (EsBuild-Based):**

Similar to the Webpack-based builder, but with a significant distinctio. it use EsBuild instead of Webpack. EsBuild, **being notably faster** due to its build in Go, offers around a **57% speed improvement** according to Angular team tests. Ideal for optimizing local development times and integrating with continuous integration workflows.

**@angular-devkit/build-angular:application (SSR Builder):**

Introduced as a new feature in Angular 17, this builder prioritizes efficient development, supporting both **server-side and client-side rendering**. Aligned with the industry trend towards server-side rendering by default, **promising enhancements in initial load times and SEO**.

## Detailed comparison:

For a more detailed understanding, let's compare **@angular-devkit/build-angular:browser** and **@angular-devkit/build-angular:browser-esbuild**. This comparison goes further than simply choosing between Webpack and EsBuild; it examines the potential impact on development speed.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709322870832/57da6b5d-e279-4db0-9b97-040d0de8eca8.png align="center")

## Conclusion:

The choice of Angular builder depends on your project's specific requirements and goals. The **Webpack-based** builder remains a solid option for many scenarios, while the **EsBuild-based** builder offers in terms of speed and efficiency. For projects demanding server-side rendering, the **@angular-devkit/build-angular:application** builder becomes to be a game changer.

Consider the aspects of your project, evaluate the builders' strengths, and make a decision based on your development needs. Remember, the key is to understand the differences of each builder and align them with your project's goals.

[Angular official documentation](https://angular.dev/tools/cli/build#)

[EsBuild comparison](https://esbuild.github.io/)