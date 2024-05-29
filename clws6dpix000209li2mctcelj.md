---
title: "Angular pipes: learning the basics"
seoTitle: "Angular Pipes: Basics Explained"
seoDescription: "Learn the basics of Angular pipes, including built-in pipes, custom pipes, and how to use them in templates and TypeScript files"
datePublished: Wed May 29 2024 18:44:11 GMT+0000 (Coordinated Universal Time)
cuid: clws6dpix000209li2mctcelj
slug: angular-pipes-learning-the-basics
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/VjWi56AWQ9k/upload/1c989332a9ffb71f00a34b3dfd237aba.jpeg
tags: webdevelopment, javascript, frontend, angularjs, web-development, angular, angular-2, webdev, typescript, frontend-development, front-end-cik5w32oi016zos53hitiymhh

---

In Angular, pipes are used to transform data in the template. It's a useful feature to save time when transforming data using complex algorithms. You can use the built-in ones, or create your own and use them throughout your application.

Angular has a lot of built-in pipes. Let's look at some of them and how to create your own.

## How it works?

The pipes are operators that you must use within the interpolation keys; you should use them in the HTML template.

Within the interpolation, you need to add `|` after the value and then the name of the pipe. A simple example would be

```xml
{{ name | uppercase }}
```

We can separate the 3 parts for better understanding

**Input**: Refers to the input value to be transformed.

**Transform**: This is the process we submit this information to.

**Output**: This is the value that results from the transformation.

> Remember, to use the built-in pipes, you need to import them into your module or your component. If you are using standalone components, import the **CommonModule**. Alternatively, you can import just the specific pipe you need instead of the whole **CommonModule**.

## Built-in pipes

Angular provides built-in pipes for typical data transformations. Here are a few examples with their explanations:

* [`DatePipe`](https://angular.dev/api/common/DatePipe): Formats a date value according to locale rules.
    
* [`UpperCasePipe`](https://angular.dev/api/common/UpperCasePipe): Transforms text to all upper case.
    
* [`LowerCasePipe`](https://angular.dev/api/common/LowerCasePipe): Transforms text to all lower case.
    
* [`CurrencyPipe`](https://angular.dev/api/common/CurrencyPipe): Transforms a number to a currency string, formatted according to locale rules.
    
* [`DecimalPipe`](https://angular.dev/api/common/DecimalPipe): Transforms a number into a string with a decimal point, formatted according to locale rules.
    
* [`PercentPipe`](https://angular.dev/api/common/PercentPipe): Transforms a number to a percentage string, formatted according to locale rules.
    
* [`AsyncPipe`](https://angular.dev/api/common/AsyncPipe): Subscribe and unsubscribe to an asynchronous source such as an observable.
    
* [`JsonPipe`](https://angular.dev/api/common/JsonPipe): Display a component object property on the screen as JSON for debugging.
    

## Using pipes with parameters

Parameters can be optional or required depending on the pipe. To specify the parameter on a pipe, you have to put it after the `:`. Let's take a look at a few examples:

The date pipe accepts parameters to control the date format:

```xml
<p>The hero's birthday is in {{ birthday | date:'yyyy' }}</p>
```

Also, the date pipe accepts a second parameter to control the timezone, you need to use another `:`

```xml
<p>The current time is: {{ currentTime | date:'hh:mm':'UTC' }}</p>
```

## Combining two pipes

You can use multiple pipes at the same time, you just have to add another `|` to separate them:

```xml
<p>The hero's birthday is in {{ birthday | date:'yyyy' | uppercase }}</p>
```

## Using pipes inside TypeScript files

Maybe you need to transform the data for some other reason and you don't need to show it in the template, you can also do it in the template, you need to add the pipe to your component's providers array and then inject it using dependency injection. After that, you can use it like this:

```typescript
const formattedDate = this.datePipe.transform(this.currentDate, 'dd/MM/yyyy');
```

## Creating our custom pipe

If the built-in pipes that Angular gives us aren't enough, you can create your own, let's see an example:

Create it using the Angular CLI:

```bash
ng g p pipes/customPipe
```

This command creates the class for your custom pipe, inside the class, you should return the transformed value.

```typescript
import { Pipe, PipeTransform } from '@angular/core';
@Pipe({
  name: 'customPipe',
  standalone: true,
})
export class CustomPipe implements PipeTransform {
  transform(value: string): string {
    return `Hello ${value}`;
  }
}
```

We just create a simple pipe that returns the value we sent plus a 'Hello' text, we make it standalone but this is not required.

```xml
<h1>{{ userName | customPipe }}</h1> //Hello Rubén
```

## Conclusion

Angular pipes are a great way to save time, by default Angular provides us with many useful pipes, but also gives us the ability to create our own. We have learned about the most useful pipes and seen an example of how to create one.