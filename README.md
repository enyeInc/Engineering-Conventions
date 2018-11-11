### Development Environment
> Make sure you are using [Node 8 or higher](https://nodejs.org/en/download/)
1. Gives you access to modern Javascript syntax
2. Provides the latest `npm`
3. `Recommended 10.0.0+`

> Make sure that ESLint is install on your IDE
* It makes sure that we are all following a [basic level of coding conventions](https://eslint.org/docs/developer-guide/code-conventions)

### Git Flow and Feature branches
> If you are working on a feature or a bug:
1. Pull the most recent master
2. Create a feature/bug branch with the following pattern `feature/[your name]/[name of feature]`
3. Example => `feature/Uche/add-new-modal` or `bug/Uche/fix-broken-navigation`

### Git Commit and Push
> You should commit you changes often and push them up to github. This serves as a backup
for your code in the event something happens to your code locally. Also, it gives your
team insight into what you are working on before the PR review process.

### Pull Requests(PR)
> PRs are the extremely important when working on a team. It allows us to have insight
on what our other team members are working on and exposes us to how they think about
code. It is crucial that you participate in the review process. Make comments, ask
questions and suggest improvements so that you and the engineer being reviewed can
grow technically and communicatively.
#### Before PR reviews
> Before you submit your code for review you should run the following commands:
1. `npm run lint`: to check your code for linting error. There should be zero.
2. `npm run test`: if there are tests, they should all be passing.
3. `npm run build`: to make sure that your code will successfully build in production.

### Commenting
Comment are a way to help not only you but any other developer that looks at your
code to better understand the logic behind you code. So comment often and frequently
1. Single comments - used for comments that are only 1 line long
    * starts with `//`
2. Multiple comments - used for comments that are more than 1 line long
    * starts with `/**` and ends with `*/`
#### Function comments
> Each and every function and class must be commented. You have to define what the
function or class does, what are its parameters and what is the expected result
* When commenting on functions/classes use [JSDoc conventions](http://usejsdoc.org/about-getting-started.html)

### File Structure
The file structure for our react components should look exactly as depicted below
```
components
└───login // folder that contains all of the components logic
│   │   actions.js // defines all redux actions used for this component
│   │   actionTypes.js // defines the actionTypes used by the actions
│   │   constants.js // defines all strings and numbers used in this component
│   │   index.js // contains all things that we want to export from the full component
│   │   reducer.js // defines all the reducers used to update the redux store
│   │   sagas.js // defines the asynchronous operation perfomed by this
│   └───components // folder that contains the main component and any sub-components that are only used within the main component (i.e buttons, modals ...)
│       │   Login.js // contains the main component react logic
│       │   Button.js // a sub-component
│       │   Modal.js // a sub-component
│       │   ...
│       │   styles.css // defines styles for the components
│       │   index.js // used to export the main component. In this case Login.js
│   
└───productsAvailable
    ...
```
#### Naming conventions
> All react components files should be capitalized and camel-cased
```
components
└───login
│   │   ...
│   └───components
│       │   Login.js // capitalized
│       │   ...
│   
└───productsAvailable
│   │   ...
│   └───components
│       │  ProductsAvailable.js // capitalized and camel-cased
│       │   ...
```

#### constants.js
> Define all strings and numbers used in a component within the `constants.js` file. This includes classnames, and url links. Add a component to describe what the constant value is for
```
/**
 * Defines the url for the database.
 *
 * @constant
 */
export const DATA_BASE_URL = 'localhost:3000';
```
#### index.js
> Each component should have an `index.js` that looks like the following:
```
import actions from './actions';
import components from './components';
import reducers from './reducers';
import sagas from './sagas';

export { actions, components, reducers, sagas };
```

#### components/index.js
> Within the `components` folder of a component there should also be another `index.js`.
Here you will import and thus apply the css stylesheet and then export the main component (*as shown below*).
```
import './styles.css';
import Login from './Login';

export { Login };
```

#### in-line styles and style.css
> [Do not use in-line styles](https://reactjs.org/docs/faq-styling.html) within any of the react components.

* Wrong way:
```
// Example.js
...
    <div style={{width: '200px', height: '100px'}} />
...
```
> Instead give the element a classname and define its style in the style sheet
* Correct way:
```
// Example.js
...
    <div className={'example-element'} />
...
```
```
// styles.css
...
.example-element {
    width: '200px';
    height: '100px';
}
...
```

### Scope
> It is very important that you do not to work on other features and bug fixes that
are outside of the request feature addition or bug fix. Keep the scope of the task
as small as possible. It makes the PR process much simpler because we know exactly
what the code under review is addressing.
