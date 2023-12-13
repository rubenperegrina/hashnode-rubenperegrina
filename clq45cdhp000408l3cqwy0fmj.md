---
title: "State management in Angular, what options are there?"
datePublished: Wed Dec 13 2023 19:10:26 GMT+0000 (Coordinated Universal Time)
cuid: clq45cdhp000408l3cqwy0fmj
slug: state-management-in-angular-what-options-are-there
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/5e2KVwyojpc/upload/0be23ed860025cef5afed8940f97601a.jpeg
tags: angularjs, web-development, angular, frontend-development, state-management

---

Managing information in our application can be challenging, especially in terms of developer experience, knowledge, and security.

Nearly all mid to large-sized applications require data management to ensure accessibility across all pages, with features for reading, adding, and editing.

Angular, being a robust framework, offers tools and libraries for streamlined state management. In this post, we will explore well-known state management solutions, customized to suit particular requirements in Angular applications.

## **1.** Stateful Services (Subjects)

Using the power of Subjects, **Stateful Services** provide a simple way to manage state within Angular. By exploring this way, developers can easily manage the state of the application just using **RxJS**, you don't need to install any third-party libraries and easily to use but has some limitations instances others.

**Example:**

```typescript
@Injectable({
  providedIn: 'root',
})
export class StatefulService {
  private stateSubject = new Subject<string>();
  state$ = this.stateSubject.asObservable();

  updateState(newState: string) {
    this.stateSubject.next(newState);
  }
}

export class MyComponent implements OnInit {
  currentState: string;

  constructor(private statefulService: StatefulService) {}

  ngOnInit() {
    this.statefulService.state$.subscribe((state) => {
      this.currentState = state;
    });
  }

  updateState() {
    this.statefulService.updateState('New State');
  }
}
```

## **2.** NgRx

NgRx Global Store is a robust state management solution inspired by **Redux**. It centralizes state and actions, providing a predictable and scalable approach to managing application data.

We can use it globally in our application or manage every single component or module with them.

> If you are using Signals in your application you can use NgRx SIgnals Store for better performance.

**Example:**

```typescript
// Actions
export const updateMessage = createAction('[App] Update Message', props<{ message: string }>());

// Reducer
const initialState = { message: '' };
const appReducer = createReducer(
  initialState,
  on(updateMessage, (state, { message }) => ({ ...state, message }))
);

// Store
export const appStore = createFeatureSelector('app');
export const selectMessage = createSelector(appStore, (state) => state.message);

// Component
export class MyComponent {
  message$ = this.store.pipe(select(selectMessage));

  constructor(private store: Store) {}

  updateMessage() {
    this.store.dispatch(updateMessage({ message: 'New Message' }));
  }
}
```

## **3.** NGXS

NGXS is a state management library that simplifies complex state management scenarios. It combines the simplicity of **Redux with Angular's reactive approach**, providing a convenient solution for developers.

```typescript
// State
export interface AppStateModel {
  message: string;
}

@State<AppStateModel>({
  name: 'app',
  defaults: { message: '' },
})
@Injectable()
export class AppState {
  @Selector()
  static getMessage(state: AppStateModel) {
    return state.message;
  }

  @Action(UpdateMessage)
  updateMessage({ patchState }: StateContext<AppStateModel>, { message }: UpdateMessage) {
    patchState({ message });
  }
}

// Action
export class UpdateMessage {
  static readonly type = '[App] Update Message';
  constructor(public message: string) {}
}

// Component
export class MyComponent {
  message$ = this.store.select(AppState.getMessage);

  constructor(private store: Store) {}

  updateMessage() {
    this.store.dispatch(new UpdateMessage('New Message'));
  }
}
```

This example uses NGXS to define a simple state with a message. It also includes an action to update the message and a selector to access the message from the component. Remember to install and configure NGXS in your application before using this code.

**There are more options like:**  
\- State adapt  
\- RxAngular  
\- MiniRx  
\- Ngx Signal State  
\- Akita  
\- Elf  
\- Custom state management

## Conclusion

Choosing the appropriate state management option for your Angular app relies on the needs of your project. Whether you prefer the easy Stateful Services or the adaptable **NgRx**, grasping these tools helps Angular developers create strong and sustainable applications.

This article gives a quick introduction to state management options in the Angular ecosystem. Try out these tools, analyze their benefits, and select the one that fits your project's requirements best.

[VSCode snippets for NgRx](https://rubenperegrina.com/vscode-snippets-for-ngrx)