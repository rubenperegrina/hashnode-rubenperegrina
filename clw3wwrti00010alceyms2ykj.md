---
title: "How to build a static blog in Angular with Scully"
datePublished: Sun May 12 2024 19:12:36 GMT+0000 (Coordinated Universal Time)
cuid: clw3wwrti00010alceyms2ykj
slug: how-to-build-a-static-blog-in-angular-with-scully
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/fMD_Cru6OTk/upload/1839ce5e42b927af92e6a03dbb579c3f.jpeg
tags: tutorial, blogging, javascript, angularjs, web-development, angular, frontend-development

---

Before I started my Hashnode blog, I tried to build my own blog. While searching for the best option, I experimented with **Scully**. Why did I choose Hashnode instead of Scully? That answer will be in another post. For now, let's concentrate on understanding what Scully is and how to build a blog using it.

%[https://github.com/rubenperegrina/scully-blog/tree/master] 

## What is Scully?

Scully is a library for Angular used to build blogs with static content. It enables you to create a **solid structure for generating a blog**. One of its best features is generating a static HTML file for each route. This functionality significantly enhances rendering **speed and SEO**.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://scully.io/" style="pointer-events: none">Check out the Scully documentation!</a></div>
</div>

## How it works?

First of all, we need an Angular application and then install the Scully library:

```bash
ng new scully-app
npm i @scullyio/scully @scullyio/ng-lib @scullyio/scully-plugin-puppeteer
```

We need to add the **ScullyLibModule** to our app.module, Scully doesn't support bootstrapping via a standalone component, Scully needs to be bootstrapped in a module, and then you can use standalone components.

There is a schematic for this:

```typescript
ng add @scullyio/init
```

With this command, we add the `ScullyLibModule` and also create the `scully.[PROJECT_NAME].config.ts`

From Angular 14 onwards the `defaultProject` property has been deprecated from the angular.json. Scully needs this property, we need to configure it:

```json
{ "defaultProject": "[PROJECT_NAME]" }
```

Finally, we need to add some scripts to our package.json:

```json
"scripts": {
    "scully": "scully",
    "scully:serve": "scully serve"
  }
```

## How to create the content?

To create content, you can use the CLI command `ng generate @scullyio/init:post --name="This is my post"` or just create the file with `.md`

This will generate the file with 3 tags:

* `title`: this is the title of the blog post
    
* `description`: this is the description
    
* `published`: this is a property representing whether the blog post is published or not. It takes a `true` or `false`.
    

Then you just have to generate the route for your post with: `npx scully`

You can also add other tags if needed, such as image, date, keywords and authors. This is useful if you want to add more features to your blog.

To test the blog, simply run: `npx scully:serve`

## Conclusion

To summarize, we have seen a brief introduction to Scully, what it is, and how it works, we need to talk more about Scully but we have a quick introduction and the first steps to building a blog with Scully, we will talk more in depth in the next articles.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://scully.io/" style="pointer-events: none">Check out the Scully documentation!</a></div>
</div>