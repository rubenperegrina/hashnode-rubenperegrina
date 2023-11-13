---
title: "Typing http error response with HttpStatusCode in Angular"
seoTitle: "How to type error response in Angular, learn how to type http errors"
seoDescription: "Learn how to type Angular httpClien errors in TypeScript, httpStatusCode, enum, 200, 400, 500, RxJS, Observable, API"
datePublished: Sat Nov 04 2023 23:00:00 GMT+0000 (Coordinated Universal Time)
cuid: clok2qiei000309l92esh7k4c
slug: typing-http-error-response-with-httpstatuscode-in-angular
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/52jRtc2S_VE/upload/725564a0e3f8c0226a0b43205bbc9d50.jpeg
tags: angularjs, web-development, typescript, frontend-development

---

Error handling is a critical aspect of web application development, and Angular provides us with powerful tools to manage errors effectively. In this article, we will dive into the world of `HttpStatusCode` in Angular HttpClient, exploring how it can streamline error management and provide `robust type safety`. You will not only learn how to handle errors efficiently but also discover how to offer clear and meaningful error messages to `enhance the user experience`.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/HttpStatusCode" style="pointer-events: none">See the article code on GitHub</a></div>
</div>

Consider this scenario: You're building a web application, and the user encounters a problem. Without proper error handling, the user may be greeted with a cryptic error message or, worse, the application may crash unexpectedly. This is where HttpStatusCode in Angular HttpClient comes to the rescue, allowing you to tackle these challenges head on.

## HttpStatusCode in Angular HttpClient

Angular HttpClient allows us to make HTTP requests to web services. When errors occur in these requests, Angular HttpClient provides an `HttpErrorResponse` object that contains error information, such as the HTTP status code. The HttpStatusCode object is a set of constants representing the most common HTTP status codes. We can see the list of errors in [Angular's page](https://angular.io/api/common/http/HttpStatusCode).

```typescript
Enum HttpStatusCode {
  Continue: 100
  Ok: 200
  Created: 201
  Accepted: 202
  NoContent: 204
  UseProxy: 305
  BadRequest: 400
    // ... (list truncated for brevity)
  Unauthorized: 401
  PaymentRequired: 402
  Forbidden: 403
  NotFound: 404
  InternalServerError: 500
  BadGateway: 502
  NetworkAuthenticationRequired: 511
}
```

## Error handling with HttpStatusCode

In this example, we use the `HttpStatusCode` object to check the response's HTTP status code of the response and provide meaningful error messages. This makes it easy to identify problems and provide clear messages to users.

```typescript
import { HttpClient, HttpErrorResponse, HttpStatusCode } from '@angular/common/http';
import { inject, Injectable } from '@angular/core';
import { catchError, throwError } from 'rxjs';
import { Product } from 'models/product.model.ts';

@Injectable({
  providedIn: 'root'
})
export class DataService {

  private http = inject(HttpClient);

  getOne(id: string) {
    return this.http.get<Product>('apiUrl/products/' + `${id}`)
      .pipe(
        catchError((error: HttpErrorResponse) => {
          if (error.status === HttpStatusCode.Conflict) {
            return throwError(() => 'Something is going wrong with the server');
          }
          if (error.status === HttpStatusCode.NotFound) {
            return throwError(() => 'The product does not exist');
          }
          if (error.status === HttpStatusCode.Unauthorized) {
            return throwError(() => 'You are not authorized');
          }
          return throwError(() => 'Oops something went wrong');
        })
      )
  }
}
```

In this code, we've harnessed the power of HttpStatusCode to gracefully handle various HTTP errors. By using HttpStatusCode, we can easily map the HTTP status codes in the error response to specific error messages that provide valuable insight to the end user.

## Prevent typos

In addition to streamlining error handling, using HttpStatusCode can help prevent typing errors by specifying the expected response types. By using get , we indicate that we expect a response that matches the Product data type. This ensures we receive correctly typed data and avoids runtime errors.

## Best practices

Here are some best practices for using HttpStatusCode effectively in the Angular HttpClient:

* `Consistency`: Maintain a consistent approach to handling errors and returning responses throughout your application.
    
* `Descriptive messages`: Ensure that your error messages are descriptive and provide users with a clear understanding of the problem.
    
* `Status code list`: Familiarize yourself with the HttpStatusCode enumeration and its associated status codes to make it easier to handle specific errors.
    

## Conclusion

The `HttpStatusCode` object in the Angular HttpClient is a valuable tool for error handling and preventing typing errors when interacting with web services. By using it effectively, we can provide descriptive messages to users and increase the robustness of our application. Use this feature to provide a better user experience and avoid unpleasant surprises when unexpected errors occur.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/HttpStatusCode" style="pointer-events: none">See the article code on GitHub</a></div>
</div>