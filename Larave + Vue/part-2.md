# Navigation using Vue Route

Before we start with the navigation part, let's talk about folder structure. As by default, laravel have folder structure well that's for laravel. For vue we'll need, or I'll say it's necessary to follow the folder structure. Here is an example you may follow:

<pre>
resources
│
├── js
│   ├── components
│   │   ├── Nav.vue
│   │   ├── Footer.vue
│   │   ├── SideBar.vue
│   │   ├── ...
│   │
│   ├── layouts
│   │   ├── App.vue
│   │   ├── ...
│   │
│   ├── pages
│   │   ├── Page1.vue
│   │   ├── Page2.vue
│   │   ├── ...
│   │
│   ├── routes
│   │   ├── index.js
│   │   ├── ...
│   │
│   ├── app.js
│   └── ...
</pre>

-  `js:` This folder likely contains all of our vue code for the project.

-  `components:` This folder is intended to store reusable Vue components. Components are modular units of code that can be used across different parts of the application.

-  `layouts:` This folder typically contains layout files that define the structure and design of different pages or sections of the application. It may include the main App.vue file, which serves as the base layout for the entire application.

-  `pages:` This folder is meant to hold individual Vue files for different pages or views of the application. Each file represents a specific page or view that the user can navigate to.

-  `routes:` This folder will contains files related to routing in the application. It may include an index.js file that defines the routes for different pages or sections of the application.

-  `app.js:` This file is the main entry point for the application. It may contain initialization code, configuration settings, or other global functionality required to start the application.

These folder structures are commonly used to organize code and separate concerns for better maintainability and modularity.

## Vue Route 

### Nav.vue
```vue
<script setup>

</script>

<template>
    <ul>
        <li><a href="#">Page 1</a></li>
        <li><a href="#">Page 2</a></li>
        <li><a href="#">Page 3</a></li>
    </ul>
</template>

<style scoped>

</style>
```

### App.vue

```vue
<script setup>
    import NavVue from '../components/Nav.vue'
</script>

<template>
    <nav-vue></nav-vue> // `nav-vue` comes from `NavVue` which we imported
    <h1>Hello LV</h1>
</template>

<style scoped>

</style>
```

### Page1.vue
```vue
<script setup>

</script>

<template>
    <h1>Page 1</h1>
</template>

<style scoped>

</style>
```
Same for other 2 pages.

### index.js
> First
```javascript
import {createWebHistory, createRouter} from "vue-router";
```

1. The  `import`  statement is used to import the  `createWebHistory`  and  `createRouter`  functions from the "vue-router" library.
2. The  `createWebHistory`  function is responsible for creating a browser history object, which allows the application to use HTML5 history mode for navigation.
3. The  `createRouter`  function is used to create a router object, which is responsible for handling the application's routes and navigation. 

> Second

```javascript
import Home from '../pages/page1.vue'
import Page2 from '../pages/page2.vue'
import Page3 from '../pages/page3.vue'
```

This code is importing three components: Home, Page2, and Page3 from their respective Vue files.

Step-wise explanation of the code:
1. The code is importing the Home component from the `../pages/page1.vue` file.
2. The code is importing the Page2 component from the `../pages/page2.vue` file.
3. The code is importing the Page3 component from the `../pages/page3.vue` file.

These imported components can be used in other parts of the code to render them on the screen or use their functionality.

> Third (creating route name, path & assigning components)
```js
const routes = [
    {
        path: '/', // Url that will show at url bar in browser
        name: 'Home', // Router name just like laravel
        component: Home, // Assign with imported routes this naming router will render
    },
    {
        path: '/page2',
        name: 'Page2',
        component: Page2,
    },
    {
        path: '/page3',
        name: 'Page3',
        component: Page3,
    },
]
```

> Lastly
```js
const router = createRouter({
    history: createWebHistory(),
    routes
})
```

Here is the full code of `index.js`:
```vue
import {createWebHistory, createRouter} from "vue-router";

import Home from '../pages/page1.vue'
import Page2 from '../pages/page2.vue'
import Page3 from '../pages/page3.vue'

const routes = [
    {
        path: '/home',
        name: 'Home',
        component: Home,
    },
    {
        path: '/page2',
        name: 'Page2',
        component: Page2,
    },
    {
        path: '/page3',
        name: 'Page3',
        component: Page3,
    },
]

const router = createRouter({
    history: createWebHistory(),
    routes: routes
})
```

Now time to add these routes to our navbar or any other links.

As in laravel we do `<a href="{{ route('home') }}">Home Page</a>` with vue we'll do "router-link".
Go to `/components/nav.vue`

Before:
```vue
<script setup>

</script>

<template>
    <ul>
        <li><a href="#">Page 1</a></li>
        <li><a href="#">Page 2</a></li>
        <li><a href="#">Page 3</a></li>
    </ul>
</template>

<style scoped>

</style>
```

After:
```vue
<script setup>

</script>

<template>
    <ul>
        <li><router-link :to="{ name: 'Home' }">Home</router-link></li>
        <li><router-link :to="{ name: 'Page2' }">Page 2</router-link></li>
        <li><router-link :to="{ name: 'Page3' }">Page 3</router-link></li>
    </ul>
</template>

<style scoped>

</style>
```

In Vue.js, you can define route links using the `router-link` component. Here's how you can define a route link:

```html
<router-link to="/home">Home</router-link>
```

In this example, `/home` is the path of the route you want to link to, and "Home" is the text that will be displayed as the link. When the link is clicked, Vue Router will navigate to the specified route.

You can also use named routes instead of specifying the path directly. Here's an example:

```html
<router-link: to="{ name: 'Home' }">Home</router-link>
```

In this case, `name: 'Home'` refers to the name of the route you want to link to. Using named routes can be useful when you have complex routing configurations. 

Still, we can't navigate to pages. We'll need to add `router-view` where we added our nav file to enable vue route to link to work.

Go to `/layouts/app.vue`

```vue
<script setup>
    import NavVue from '../components/nav.vue'
</script>

<template>
    <nav-vue/>
    <router-view></router-view>
    <h1>Hello LV</h1>
</template>

<style scoped>

</style>
```
Then ar `app.js` file before we mount `#app` we'll import and use that before mount

Import route:
```vue
import router from './router/index.js';
```

Form:
```vue
createApp(App).mount('#app');
```

To:
```vue
createApp(App).use(router).mount('#app');
```
Complete code:

```vue
import './bootstrap';

import { createApp } from "vue";
import router from './router/index.js';
import App from "@/layouts/app.vue";

createApp(App).use(router).mount('#app');
```

Though we're using route to `app.js`. It doesn't get anything from `index.js` file. That is because at vue we need to export route from index.js file.

Go to `/routes/index.js` & add at the end (meaning at the end of everything at the file):

```vue
export default router;
```

That's it!!
Now page navigation should work perfectly.
