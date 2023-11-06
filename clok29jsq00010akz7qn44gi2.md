---
title: "VSCode snippets for NgRx"
datePublished: Sat Nov 04 2023 13:09:10 GMT+0000 (Coordinated Universal Time)
cuid: clok29jsq00010akz7qn44gi2
slug: vscode-snippets-for-ngrx
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/K4c8RymNeu8/upload/fe3be41a090bf2bc5ead838c9365d15c.jpeg
tags: angularjs, web-development, typescript, ngrx, vscode-cjevho8kk00bo1ss2lmqqjr51

---

When working with NgRx it is common to have to go to the [official documentation](https://ngrx.io/guide/store) to copy reducers or sample actions so that we don't have to write them by hand, there is a better way to save time.

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/vscode-ngrx-snippets" style="pointer-events: none">See the article code on GitHub</a></div>
</div>

## **Adding our own snippets**

To add our own snippet in VSCode we have to go to `View` -&gt; `Command Palette`, search for `user snippets` press Enter and then search for `TypeScript`, this is where we have to add our shortcuts (remember if you already have some shortcuts in this folder don't overwrite them).

## **My NgRx snippets**

This json file are the snippets I use when developing with NgRx, having them quickly saves you a lot of time in not having to look at the documentation, they are snippets for: `Print to console`, `Actions`, `Reducer` and `App Reducer`.

```json
{
    // Place your snippets for typescript here. Each snippet is defined under a snippet name and has a prefix, body and 
    // description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
    // $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
    // same ids are connected.
    // Example:
    // "Print to console": {
    //     "prefix": "log",
    //     "body": [
    //         "console.log('$1');",
    //         "$2"
    //     ],
    //     "description": "Log output to console"
    // }
    "Print to console": {
        "prefix": "clog",
        "body": [
            "console.log $1",
        ],
        "description": "Log output to console"
    },

    "NgRx Actions": {
        "prefix": "ngrx-actions",
        "body": [
            "import { createAction } from '@ngrx/store';",
            "",
            "export const ${1:increment} = createAction('[${2:Counter Component}] ${1:Increment}');",
        ],
        "description": "Crea las acciones de NgRx"
    },

    "NgRx Reducer": {
        "prefix": "ngrx-reducer",
        "body": [
            "import { createReducer, on } from '@ngrx/store';",
            "import { $2 } from './${1:counter}.actions';",
            "",
            "export interface State {",
            "    ${3:key}: ${4:String}; ",
            "}",
            "",
            "export const initialState: State = {",
            "   ${3:key}: ${5:'hola'},",
            "}",
            "",
            "const _${6:counter}Reducer = createReducer(initialState,",
            "",
            "    on(${2:increment}, state => ({ ...state, ${3:key}: ${5:'hola'}})),",
            "",
            ");",
            "",
            "export function ${6:counter}Reducer(state, action) {",
            "    return _${6:counter}Reducer(state, action);",
            "}"
        ],
        "description": "Crea el reducer básico"
    },


    "NgRx App Reducer": {
        "prefix": "ngrx-app-reducers",
        "body": [
            "import { ActionReducerMap } from '@ngrx/store';",
            "import * as $1 from './$2.reducer';",
            "",
            "",
            "export interface AppState {",
            "   ${3:todos}: $4",
            "}",
            "",
            "",
            "",
            "export const appReducers: ActionReducerMap<AppState> = {",
            "   ${3:todos}: $5,",
            "}",
        ],
        "description": "Crea el AppReducer principal"
    },

}
```

## **How to use snippets in VSCode**

Once we have saved our snippets in the VSCdode user configuration, it is as easy as in any `.ts` file to write the shortcut we have set, in this case we have `clog`, `ngrx-actions`, `ngrx-reducer` and `ngrx-app-reducer`.

## **Conclusion:**

In summary, Ngrx snippets in Visual Studio Code expedite development, diminish errors, and foster consistency in projects. They are valuable tools for developers of all levels, enhancing code quality and providing flexibility to cater to specific needs. Incorporating snippets into your workflow can be a smart choice for optimizing your Ngrx productivity

<div data-node-type="callout">
<div data-node-type="callout-emoji">🚀</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/rubenperegrina/vscode-ngrx-snippets" style="pointer-events: none">See the article code on GitHub</a></div>
</div>