# Development Environment
#### Node and NPM
Make sure you are using [Node 10 or higher](https://nodejs.org/en/download/)
1. Gives you access to modern Javascript syntax
2. Provides the latest `npm`
3. `Recommended 12.0.0 LTS`

#### Javascript Linting
Install ESLint in your Repo and IDE
* It assures that you are following a [basic level of Javascript coding conventions](https://eslint.org/docs/developer-guide/code-conventions)

#### Prettier
Install Prettier in your Repo
* It assures that you have a [consistent way to format code](https://prettier.io/docs/en/install.html)

# Git Work Flow
#### Feature branches
Leverage [feature branches](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow) whenever you want to add a feature or fix a bug.
1. Pull the most recent master
2. Create a feature/bug branch with the following pattern `feature/[your name]/[name of feature]`
3. Example => `feature/Uche/add-new-modal` or `bug/Uche/fix-broken-navigation`

#### Commit and Push
When working on a feature make sure to commit and push your changes to the remote branch as often as possible.
* This assures that your commits are small and manageable.
* Additionally, in the event of system failure or any random that affects your local code, you will have a fairly recent backup of your code in the remote branch.

#### Before Pull Requests
Before you create a pull request, run the following commands locally:
1. `npm run lint`: to check your code for linting errors. There should be zero.
2. `npm run test`: if there are tests, they should all be passing.
3. `npm run build`: to make sure that your code will successfully build in production.

#### Pull Requests (PR)
After you have finished working on your feature or bug fix, you should [create a pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) from your feature branch to the master branch.
* This PR allows you to see the difference between the current master code and the feature code that you want to merge into the master.
* This process is very important because it allows your teammates to review your code in order make sure that it is consistent with coding conventions and make potential suggestions to improve the code quality.

#### Pull Request Maximum Changes
Each PR should contain small and specific code changes. It is difficult for your teammates to review your code when they are many changes all pushed into one Pull Request. Therefore, you must absolutely abide by the following rules:
* All Pull Requests can contain at most `500 changes`.
* If your PR contains more than `500 changes`, you must break down this PR into smaller different PRs.

#### Review All Pull Requests
It is required that each member of your team review and comment on every PR that is created. This makes sure that:
*  You are keeping your teammates accountable for the quality of the code that they are writing.
* The code merged into your master meets the highest of standards.
* You are learning from the code that your teammates are writing.

#### Merging Pull Requests
The scrum master is the only one that can merge a pull request.

# More Coding Conventions
#### The DRY KISS principle
It is important to write clean, self teaching code. You can achieve by making sure that your code is both moduluar and simple to understand.
* DRY - Keep logic short, and divided into reuseable units
* KISS - Keep code simple and straightforward for other humans to understand. 

[DRY KISS](https://dzone.com/articles/software-design-principles-dry-and-kiss)

#### Comment Your Code
Comments help, not only you but, others developer better understand the logic behind your code. It is essential that you comment often and frequently.
1. Single comments - used for comments that are only 1 line long
    * starts with `//`
2. Multiple comments - used for comments that are more than 1 line long
    * starts with `/**` and ends with `*/`

[JSDocs With Typescript](https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html)

#### Typescript
Typescript enforces strict variable types and gives engineers insights into potentially breaking type related bugs. It assures that your code is more readable and predicatable. All javascript code should be written in typescript.
* [Best Practices with Typescript](https://www.typescriptlang.org/docs/handbook/declaration-files/do-s-and-don-ts.html)

#### Styles
[Do not use in-line styles](https://reactjs.org/docs/faq-styling.html) within any of the react components. Instead, give the element a `className` and define its style in the style sheet.

* Incorrect:
```
// Example.ts
...
    <div style={{width: '200px', height: '100px'}} />
...
```

* Correct:
```
// Example.ts
...
    <div className='example-element' />
...


// styles.scss
...
.example-element {
    width: '200px';
    height: '100px';
}
...
```

#### Class Names
Class names should be consistent and explicit. By following, the [ABEM](https://css-tricks.com/abem-useful-adaptation-bem/) methodology you will accomplish both.

#### File Structure
The file structure for our react components should look exactly as depicted below
```
components
├── login // component folder
│   │   ├── constants.ts // all components strings and numbers
│   │   ├── index.ts // the component exportables
│   │   └── types.ts // the component type definitions
│   │
│   ├── hooks // the custom hooks for this component
│   │   ├── index.ts // exports the hooks
│   │   └── useExampleHook.ts // example custom hook
│   │   
│   └── components // the main component and sub-components folder
│       ├── Login.ts // the main component
│       ├── Button.ts // a sub-component
│       ├── Modal.ts // a sub-component
│       ├── ...
│       ├── styles.scss // components styles
│       └── index.ts // exports the main component.
│   
└── productsAvailable
    ...
```

#### File Naming Component Files
All react components files should start with a capitalized letter and the rest of the name should be camel-cased.
```
components
├── login
│   │   ...
│   └── components
│       ├── Login.ts // capitalized
│       │   ...
│   
├── productsAvailable
│   │   ...
│   └── components
│       ├── ProductsAvailable.ts // capitalized and camel-cased
│       │   ...
```

#### Constants File
Define all strings and numbers used in a component within the `constants.ts` file. Add a comment that describes the constant.

```
/**
 * Defines the url for the database.
 *
 * @constant
 */
export const TEST_URL = 'localhost:3000';
```

* The only exception is `classNames`. These strings should be defined in the component directly.

#### Index File
Each component should have an `index.ts` that looks at a minimun like the following:
```
import components from './components';
import hooks from './hooks';
import types from './types';

export { components, hooks, types };
```

#### Components Folder's Index File
Within the `components` folder of a component there should also be an `index.ts` file.
Here you will import the css stylesheet and then export the main component (*as shown below*).
```
import Login from './Login';

import './styles.scss';

export default { Login };
```

# React
#### Hooks
[React Hooks](https://reactjs.org/docs/hooks-intro.html) allow for more reusable and modular react code. Use them in the following cases:
* All async operations (i.e. API requests, timer operations, interacting with localstorage etc...)
* Handling component specific state
* Abstracting complex component logic
* Handling reuseable stateful logic

#### Functional Components
Use functional components over class components for the following reasons
* They are more concise and performant
* They do not require lifecycle management
* React hooks only work with functional components

[Why Functional Components](https://habr.com/en/post/443500/)

# API Endpoint
When writing endpoints, it is important that there is a predictable standard that the frontend and backend use in order to make communication consistent. Leverage the standards of the [jsend](https://github.com/omniti-labs/jsend) to achieve this consistency.

```
// GET users request - success

{
    status : "success",
    data: {
        users: [{ id: 1, name: 'test'}, { id: 2, name: 'test2' }],
    },
}

// GET users request - error

{
    status : "error",
    message: "some error message",
}
```

#### HTTP Status Codes
Use the [http-status-codes](https://www.npmjs.com/package/http-status-codes) library when defining status codes and messages.
