# Setting Up Laravel with Vue 3 and Vite

This setup will enable you your starting point vue with laravel. In this tutorial there won't be separate front-end and back-end. What I mean is there won't be 2 different project to handle front-end and back-end. 

We'll use single laravel app where we'll handle backend with laravel and front-end with vue. 

When I started laravel with vue I got confused with many thing like for example routes or auth why need to use vue route, can't just use laravel route?. If you worked with laravel long time then try vue then you may wonder it's easy with laravel this component or that components.

But after working sometime I'll say just remember that those components the way those work already present to vue. So try to use front-end's all the staffs using vue.

Well after writing this far I don't know why I wrote these since we are here to implement vue with laravel ;D Anyway just don't be confused like me anyway.

I assumed you've worked with laravel & saw a bunch of vue tutorial but yet to apply or already did some small project with vue.

## Step 1: Laravel Installation

Let's say our app name is `Blog`. Then,

```composer log
composer create-project laravel/laravel blog
```

## Step 2: Vue and Vite Setup

In your Laravel project directory, open a command prompt and install Vue 3 and Vite dependencies by running:

```composer log
npm install vue@next vue-loader@next
```

## Step 3: Configure Vue in app.js

```composer log
import { createApp } from "vue";
```

## Step 4: Create Layouts Folder and app.vue

Inside the `resources/js` directory, create a new folder named `layouts`. Inside this folder, create a file named `app.vue`. This will serve as the main layout for your Vue components. Just like master blade file for other blade files.

## Step 5: Import Layout in app.js

Go back to the app.js file and import the app.vue layout you just created:

```composer log
import App from "@/layouts/app.vue";
```

You can also like below,

```composer log
import App from "./layouts/app.vue";
```

Then, create and mount the Vue app with the imported layout:
```composer log
createApp(App).mount('#app');
```

## Step 6: Create a Blade File

In the resources/views directory, create a new blade file, for example, welcome.blade.php. Add the following content to this file, incorporating Vue into your Laravel Blade template:

```html
<!doctype html>
<html lang="en">
<head>
    @vite(['resources/css/app.css', 'resources/js/app.js'])
</head>
<body>
    <div id="app"></div>
</body>
</html>
```

## Step 7: Install Vite Plugin

Install the Vite plugin for Vue by running the following command:

```composer log
npm install @vitejs/plugin-vue
```

## Step 8: Configure Vite in vite.config.js

Open the vite.config.js file in your project root directory. Import the vue plugin at the top:

```composer log
import vue from '@vitejs/plugin-vue';
```

Inside the plugins section of the config, add the vue() plugin:
```javascript
export default defineConfig({
    plugins: [
        vue(),
        // ...other plugins
    ],
});
```

## Step 9: Compile and Run

Now you're ready to compile and run your application. In the command prompt, run:

```composer log
npm run dev
```

This command will initiate the Vite development server, and your Laravel application with Vue 3 integration should be up and running.

This setup allows you to leverage the power of Vue 3 and Vite's fast development experience within your Laravel application. If you encounter any issues or have questions, feel free to seek further assistance to CharGPT, Google, Community, Stackoverflow, Youtube. Happy coding!
