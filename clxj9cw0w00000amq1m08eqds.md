---
title: "Generate documentation for your Angular application with Compodoc"
seoTitle: "Generate Angular Docs with Compodoc"
seoDescription: "Generate Angular application documentation effortlessly with Compodoc. Learn setup, features, and benefits"
datePublished: Mon Jun 17 2024 17:37:18 GMT+0000 (Coordinated Universal Time)
cuid: clxj9cw0w00000amq1m08eqds
slug: generate-documentation-for-your-angular-application-with-compodoc
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Y7d265_7i08/upload/11ad14e6a31ae8e941c631b442d3fdb4.jpeg
tags: webdevelopment, javascript, frontend, angularjs, web-development, angular, angular-2, documentation, webdev, typescript, frontend-development, compodoc

---

One of the tasks that every developer hates is documenting. We know that it is very important and could be helpful in the future, but it's a tedious task.

Documentation is another part of development, the same as taking the recruitment, development, QA, etc. Documenting our application **helps with onboarding new teammates, fixing future issues and better understanding the project**. In this article, we will learn about what Compodoc is, its main features, how to set it up and more.

## What is Compodoc?

Compodoc is a documentation tool for Angular applications. **It generates static documentation of your application automatically**. Once it is configured, you don't have to do anything more.

Compodoc has support for [**Angular**](https://angular.io/), [**NestJS**](https://nestjs.com/), and [**Stencil**](https://stenciljs.com/), 8 themes with integrated dark mode, support for 12 languages, and many more features.

## Installation and configure

The installation is easy; we just run the following command:

Angular CLI:

```bash
ng add @compodoc/compodoc
```

or NPM:

```bash
npm install -g @compodoc/compodoc
```

This command will create a `tsconfig.doc.json` file. In this file, we have to decide which parts of our application we want to include or exclude.

```json
{
  "include": ["src/**/*.ts"],
  "exclude": ["src/test.ts", "src/**/*.spec.ts", "src/app/file-to-exclude.ts"]
}
```

Also, we can add a few scripts to execute our documentation:

```json
"compodoc:build": "compodoc -p tsconfig.doc.json",
"compodoc:build-and-serve": "compodoc -p tsconfig.doc.json -s",
"compodoc:serve": "compodoc -s"
```

## The results

Once we have installed and configured our project, everything is done. We just need to run the serve script and see what Compodoc builds. Let's take a look at a few examples:

![Screenshot of the SoundCloud-ngrx documentation overview page. The left sidebar contains navigation links such as README, CHANGELOG, LICENSE, and various sections like Modules, Components, Classes, and more. The main section displays a diagram of the application structure with components and modules interconnected, and buttons for zooming in, resetting, and zooming out. Below the diagram, there are icons indicating the number of Modules, Components, Injectables, Pipes, Classes, and Interfaces.](https://cdn.hashnode.com/res/hashnode/image/upload/v1714388825605/b26afa49-b6bb-42b7-bc69-911b39428253.png align="center")

> In the project overview, we have a sidebar menu with all of our modules, components, classes, interfaces, etc.

![A screenshot of the coding frontend documentation generated using Compodoc. The left sidebar includes sections like Getting started, Modules, Components, Classes, Injectables, Interfaces, Pipes, Routes, Miscellaneous, and Documentation coverage. The main content shows a detailed routing module tree diagram with various routes and components, such as AppRoutingModule, FightRoutingModule, HomeRoutingModule, and StartRoutingModule, along with their respective paths and components.](https://cdn.hashnode.com/res/hashnode/image/upload/v1714389093660/c9942bc3-75fc-4fa3-a3d2-52b0187cfdbc.png align="center")

> Routing overview, we have a detailed map with all of our routes.

![A screenshot of a documentation page for the "IconButtonComponent" in a software project. The page includes a navigation menu on the left and details about the component on the right, such as file path, metadata, and a code snippet for the button template.](https://cdn.hashnode.com/res/hashnode/image/upload/v1714388974646/f54e5532-cfa1-47e8-81a5-210f24153cc0.png align="center")

> Component overview, detailed information of each component.

![A screenshot of a documentation coverage report generated using Compodoc. The report shows a list of files with their types, identifiers, and documentation coverage percentages. The coverage is color-coded: green for high coverage, yellow for partial coverage, and red for no coverage. The overall documentation coverage is 1%. The sidebar on the left includes sections like Overview, README, CHANGELOG, LICENSE, Dependencies, Modules, Components, Classes, Injectables, Interfaces, Pipes, Miscellaneous, Routes, and Documentation coverage.](https://cdn.hashnode.com/res/hashnode/image/upload/v1714389001838/f50dc745-82cb-4da5-be21-b3acc8791db6.png align="center")

> Documentation coverage to have the knowledge of which percentage we have documented.

## Conclusion

We just built our project documentation in a few steps. Compodoc, as you can see, is a great tool, fully automated to create your project documentation. We only saw a few features, but Compodoc has a lot more. We will talk more about **Compodoc** in the next articles.

I have attached the official page below.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://compodoc.app/" style="pointer-events: none">Check out the Compodoc official page!</a></div>
</div>