# React-Semantic.UI-Starter

## Out-of-box:

![](https://github.com/Metnew/react-semantic.ui-starter/blob/for-gh/screen.gif)

## DEMO: [You can find it here](https://metnew.github.io/react-semantic.ui-starter/)

[![Build Status](https://travis-ci.org/Metnew/react-semantic.ui-starter.svg?branch=master)](https://travis-ci.org/Metnew/react-semantic.ui-starter) [![codecov](https://codecov.io/gh/Metnew/react-semantic.ui-starter/branch/master/graph/badge.svg)](https://codecov.io/master/Metnew/react-semantic.ui-starter) [![David](https://img.shields.io/david/Metnew/react-semantic.ui-starter.svg)]() [![David](https://img.shields.io/david/dev/Metnew/react-semantic.ui-starter.svg)]() [![Known Vulnerabilities](https://snyk.io/test/github/metnew/react-semantic.ui-starter/badge.svg)](https://snyk.io/test/github/metnew/react-semantic.ui-starter) [![Issue Count](https://codeclimate.com/github/Metnew/react-semantic.ui-starter/badges/issue_count.svg)](https://codeclimate.com/github/Metnew/react-semantic.ui-starter) [![Code Climate](https://codeclimate.com/github/Metnew/react-semantic.ui-starter/badges/gpa.svg)](https://codeclimate.com/github/Metnew/react-semantic.ui-starter)

### What is it?
Production-ready, performance-first, optimized, robust, fully-featured boilerplate/example for your **new Progressive Web App**.

#### Lighthouse result - [you can find it here](https://googlechrome.github.io/lighthouse/viewer/?gist=cd19fc335d4dc2abfbba10ee550bd0c8)
SPOILER: 97/100. It might be better/worse in your browser.

#### DOMContentLoaded, and etc:
When app is cached with Service Workers:
<img src="https://github.com/Metnew/react-semantic.ui-starter/blob/for-gh/after-cached.png" />

#### Includes:

- **[React](https://facebook.github.io/react/)** and **[Redux](http://redux.js.org/)**
- **[React-Router v4(!)](https://github.com/ReactTraining/react-router)** + **[React-Router-Redux v5(!)](https://github.com/reactjs/react-router-redux)**
- **[JSON-server](https://github.com/typicode/json-server)** - mock db.
- **[Redux-thunk](https://github.com/gaearon/redux-thunk)** and **[Redux-Devtools-Extension](https://github.com/zalmoxisus/redux-devtools-extension)**
- **[Fetch polyfill](https://github.com/github/fetch)**
- **[Semantic-ui-react](http://react.semantic-ui.com/)** - UI components.
- **[Store2](https://github.com/nbubna/store)** - LocalStorage access.
- **[Webpack 2](https://webpack.js.org)**:
    - babel (stage-0),
    - **HMR**, devServer, hotMiddleware,
    - better code optimization with **[Babel React Optimize](https://github.com/thejameskyle/babel-react-optimize)**,
    - Remove unused css with **[purifycss-webpack](https://github.com/webpack-contrib/purifycss-webpack)**
- **[Jest](https://facebook.github.io/jest/)** and **[Enzyme](https://github.com/airbnb/enzyme)** - awesome libraries for testing.
- **[why-did-you-update](https://github.com/garbles/why-did-you-update)** and **[React-Addons-Perf](https://facebook.github.io/react/docs/perf.html)** for better performance optimization.
- **[Lodash](https://lodash.com/)** - is a dependency of Semantic-ui-react, but with tree-shaking and **[lodash-webpack-plugin](https://github.com/lodash/lodash-webpack-plugin)** you import in your bundle only code that you use.
- **[Offline-plugin](https://github.com/NekR/offline-plugin)**, **[webpack-manifest-plugin](https://github.com/danethurber/webpack-manifest-plugin)** and **[preload-webpack-plugin](https://github.com/GoogleChrome/preload-webpack-plugin)** for your next progressive app.
- [And more tools for building and testing...](https://github.com/Metnew/react-semantic.ui-starter/blob/dev/package.json)

### Usage

#### Install:
```bash
git clone https://github.com/Metnew/react-semantic.ui-starter.git
cd react-semantic.ui-starter && rm -rf .git  
npm install
```

#### Run:

```bash
npm run dev # run app in dev mode
npm run db  # run mock db for app(from another process)
```

#### Build:

```bash
npm run build # build app
npm run build:demo # build with process.env.BUILD_DEMO = true
```

It generates `dist` folder.

#### Test:

```bash
npm run test # run tests with Jest
```

### FAQ

##### Where is manifest.json?
You can find it in `webpack_config/config.js`

##### Is SSR available?
It's under active development inside `/server` folder.

##### How it differs from other starters?
Performance-first.    
**Main purpose - build highly customizable skeleton for PWA, with SSR, following best practices.**

##### Is it official starter from semantic-ui-react ?
No, (currently no, but maybe... :wink:).

##### "You have a components folder and containers folder..and in the container you have another components folder?"

Components inside `containers/**/components` are components that are required by container.     

For example, `Dashboard`(container) has `DashboardComponent`(component). You can think about `DashboardComponent` as "Isolated component", it isn't used in app anywhere except own parent-container.

Components in components are components that:
1. Don't have own logic and connection with state (as opposite to containers)
2. Aren't "isolated".(!)

As your app's components will increase in size, it can be refactored to similar structure that currently implemented in - [semantic-ui-react]( https://github.com/Semantic-Org/Semantic-UI-React/tree/master/src).

##### JSON-server? Why?
Maybe it will be useful for some purposes in your project.

### Where are tests?
There are tests for actions and for reducers.    
Each reducer/action has own folder, where you can find:
1. Reducer/action itself.
2. Tests for it.

### How to write tests?
You can find [action testing example here](https://github.com/Metnew/react-semantic.ui-starter/blob/dev/common/actions/auth/index.test.js)         
It uses [redux-mock-store](https://github.com/Metnew/react-semantic.ui-starter/blob/dev/common/actions/auth/index.test.js)

### How Auth works?
Migration from React-Router v3 to v4 may cause some problems.     
There is no `onEnter` props in `Route` component.    

So, we can solve it that way:
1. Implement [global routing object.](https://github.com/Metnew/react-semantic.ui-starter/blob/dev/common/routing/index.jsx#L9)
2. Implement [RouteAuth](https://github.com/Metnew/react-semantic.ui-starter/blob/dev/common/components/RouteAuth/index.jsx) component that protects child component from unauthorized users.
3. Pass function that checks is user allowed to visit route as prop [in every `RouteAuth` component.](https://github.com/Metnew/react-semantic.ui-starter/blob/dev/common/routing/index.jsx#L52)
4. When RouteAuth renders [it calls that function.](https://github.com/Metnew/react-semantic.ui-starter/blob/dev/common/routing/index.jsx#L52)
5. As [`authCheck` function can call redux store](https://github.com/Metnew/react-semantic.ui-starter/blob/dev/common/components/Root/index.jsx#L19-L30), we can access redux's state before `Route` is rendered.
6. Profit!!!!!
7. We have access to redux state in function that allows `Route` to be rendered.
8. Also, there is an additional handler for [auth logic in App container.](https://github.com/Metnew/react-semantic.ui-starter/blob/dev/common/containers/App/index.jsx#L178-L184)

### How built app looks?
**[Like this.](https://github.com/Metnew/react-semantic.ui-starter/tree/gh-pages)**

### Also:

[Unstable branch with **latest features.**](https://github.com/Metnew/react-semantic.ui-starter/tree/dev)

> Have a question? Ask it. :wink:

PRs, and issues are welcome :smiling_imp:

### Author

Vladimir Metnew <vladimirmetnew@gmail.com>

### LICENSE

MIT
