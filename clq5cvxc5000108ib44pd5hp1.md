---
title: "Playing with Google's Gemini Pro API"
datePublished: Thu Dec 14 2023 15:29:22 GMT+0000 (Coordinated Universal Time)
cuid: clq5cvxc5000108ib44pd5hp1
slug: playing-with-googles-gemini-pro-api
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/NnYbRvZUi9A/upload/af5524f180b07054d6597f2f7398c75a.jpeg
tags: ai, angularjs, web-development, angular, apis, google, frontend-development, ai-tools, chatgpt, promptengineering, gemini

---

Last week, **Google announced its own biggest and most powerful AI**, which was a bit controversial because it was announced with comparisons against **OpenAI's ChatGPT**, in most of the comparisons Google's AI came out on top.

After a year with ChatGPT among us, it seems that the first real competition is coming out.

Not only have they presented Gemini, as it's called, but from day one they've opened up the API to use it, they've provided a **free API key for development purposes**, which is great!

In this article, we are going to test the capabilities of Gemini using its API.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/google-gemini-pro-ai" style="pointer-events: none">See the article code on GitHub</a></div>
</div>

## How to get the API key?

Go to [https://ai.google.dev/](https://ai.google.dev/) and obtain your API key

Once we have the key we need to create a project to use it, in this case, we are going to use [Angular](https://rubenperegrina.com/whats-new-in-angular-17).

## Creating our Gemini project

First, we will create our project to be able to use **Gemini**, I assume you have everything you need to work with Angular installed, if not you can see it here:

[https://angular.dev/tutorials/first-app](https://angular.dev/tutorials/first-app)

We will create our project using Angular CLI:

```typescript
ng n google-gemini-pro-ai
```

## Installing Gemini library

Install the **Google Gemini library** with the following command:

```typescript
npm i @google/generative-ai
```

Make sure everything goes well and check your package.json to see if the **@google/generative-ai** is installed.

## Using the Gemini API

The last and most important part, inside our component where we will display the results, we create a new `GoogleGenerativeAI`, is imported from the library we have installed.

```typescript
import { GoogleGenerativeAI } from '@google/generative-ai';
import { environment } from '../environments/environment';
generativeAI = new GoogleGenerativeAI(environment.gemini_api_key);
```

`GoogleGenerativeAI` gets the API key, in this case, we have set it in the environments.

> You can generate your own environments with ng g environments

Then we have to choose the model we are going to use, we choose it by calling `getGenerativeModel` on our `GoogleGenerativeAI` that we have generated before, I expect to get a model, so we choose **gemini-pro.**

```typescript
model = this.generativeAI.getGenerativeModel({ model: 'gemini-pro' });
```

In this example I have added an input so that the user can add their prompt, the result will be displayed on the screen.

```typescript
  <h1> Google Gemini pro </h1>
  <label for="prompt">Type your prompt</label>
  <br><br>
  <input id="prompt" [(ngModel)]="prompt" placeholder="Enter your prompt here" />
  <button (click)="generate()" [disabled]="!prompt">Generate!</button>
  <br><br>
  @defer (when result) {
    {{ result }}
  }
  @placeholder {
    <span>Waiting for your prompt</span>
  }
  @loading(minimum 1s) {
    <span>Loading...</span>
  }
```

When the user adds the prompt and clicks the generate button, it calls the function that calls the Gemini API.

```typescript
  async generate() {
    try {
      const result = await this.model.generateContent(this.prompt);
      const response = await result.response;
      this.result = response.text();
    } catch(e: any) {
      this.result = e;
    }
  }
```

Simply with our model created, we need to call `generateContent` passing the user prompt, it will return the result or an error, we control this with the [new defer blocks](https://rubenperegrina.com/how-does-angulars-new-control-flow-work).

## Conclusion

That's all, with just a few lines we can start using the Gemini Pro API, this is a simple example where we have just used text with a simple answer, in the following articles I will make examples with **data stream to make a chat, answers with images and everything that this API allows us to do**.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/google-gemini-pro-ai" style="pointer-events: none">See the article code on GitHub</a></div>
</div>