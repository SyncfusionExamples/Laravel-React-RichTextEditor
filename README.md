# How to Integrate Syncfusion EJ2 React Components in Laravel project
The following steps is used to Integrate Syncfusion EJ2 React Rich Text Editor in Laravel using Vite.

Skip to the getting started section if you have already configured the environment.

## Prerequisites

Before getting started with Syncfusion React Rich Text Editor component in Laravel using Vite, check whether the following are installed in the developer machine.
* [PHP](https://www.php.net/downloads.php) - To download PHP.
* [Node.js](https://nodejs.org/en/download/) - To download Node.js.
* [Laravel](https://laravel.com/docs/8.x/installation) - To install Laravel.
* [Composer](https://getcomposer.org/download/) - To install Composer.
* [Vite](https://vitejs.dev/guide/#scaffolding-your-first-vite-project) - To install Vite.

## Setting up the environment

#### For Windows users

### 1. Install PHP

* Download the PHP from the [official website](https://windows.php.net/download#php-8.2).

### 2. Install Composer

* Download the Composer from the [official website](https://getcomposer.org/download/).

### 3. Install Laravel

* Open the command prompt and run the following command to install Laravel.

```bash
composer global require laravel/installer
```

## Create a Laravel project


#### For Windows users

```bash
laravel new example-app
```

Now change the directory to the example-app folder.

```bash
cd example-app
```


## Getting started from Laravel Project

### 1. Install dependencies
This section describes how to add the React, EJ2
In the command prompt, run the following commands to install the dependencies.

If you are cloning the github repository please goto Run the project.

Install the dependencies of the laravel project.
```bash
composer install
```
If you are getting any error while installing the dependencies, run the following command.
```bash
composer install --ignore-platform-req=ext-fileinfo
```

Install the React js dependencies.
```bash
npm install react react-dom @vitejs/plugin-react 
```
Install the Syncfusion EJ2 React Rich Text Editor package.
```bash
npm install @syncfusion/ej2-react-richtexteditor
```

### 2. Configure the vite.config.js file
Add the following code to the vite.config.js file in the root directory of the project.
```js
import { defineConfig } from "vite";
import laravel from "laravel-vite-plugin";
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [
    laravel({
      input: ["resources/css/app.css", "resources/js/app.jsx"],
      refresh: true,
    }),
    react(),
  ],
});

```

### 3. Add the root element to the welcome.blade.php file
Add the root element to the welcome.blade.php file in the resources/views folder.
``` html
<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">

        <title>Laravel</title>

        <!-- Fonts -->
        <link rel="preconnect" href="https://fonts.bunny.net">
        <link href="https://fonts.bunny.net/css?family=figtree:400,600&display=swap" rel="stylesheet" />
        
        @vite(['resources/js/app.jsx', 'resources/css/app.css'])
        <!-- Styles -->
        <link href="https://cdn.syncfusion.com/ej2/material.css" rel="stylesheet">       
        </style>
    </head>
    <body class="antialiased">
        <div id="app"></div>
    </body>
</html>

```

### 4. Add the following code to the app.jsx file to mount the React application

Rename the `app.js` to `app.jsx` and mount the React component.
```js
//Import and create a React root component
import React from "react";
import ReactDOM from "react-dom";
import Welcome from "./Welcome";

ReactDOM.render(<Welcome />, document.getElementById("app"));

```

### 5. Create a Welcome.React file in the resources/js folder and add the following code
```jsx

import { HtmlEditor, Image, Inject, Link, QuickToolbar, RichTextEditorComponent, Toolbar } from '@syncfusion/ej2-react-richtexteditor';
import * as React from 'react';
function Welcome() {
    let rteObj;
    return (<div className='control-pane'>
            <div className='control-section' id="rte">
                <div className='rte-control-section'>
                    <RichTextEditorComponent id="defaultRTE" ref={(richtexteditor) => { rteObj = richtexteditor; }}>
                        <p>The Rich Text Editor component is a WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
                        <p><b>Key features:</b></p>
                        <ul>
                            <li>
                                <p>Provides &lt;IFRAME&gt; and &lt;DIV&gt; modes</p>
                            </li>
                            <li>
                                <p>Capable of handling markdown editing.</p>
                            </li>
                            <li>
                                <p>Contains a modular library to load the necessary functionality on demand.</p>
                            </li>
                            <li>
                                <p>Provides a fully customizable toolbar.</p>
                            </li>
                            <li>
                                <p>Provides HTML view to edit the source directly for developers.</p>
                            </li>
                            <li>
                                <p>Supports third-party library integration.</p>
                            </li>
                            <li>
                                <p>Allows a preview of modified content before saving it.</p>
                            </li>
                            <li>
                                <p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p>
                            </li>
                            <li>
                                <p>Contains undo/redo manager.</p>
                            </li>
                            <li>
                                <p>Creates bulleted and numbered lists.</p>
                            </li>
                        </ul>
                        <Inject services={[HtmlEditor, Toolbar, Image, Link, QuickToolbar]}/>
                    </RichTextEditorComponent>
                </div>
            </div>
        </div>);
}
export default Welcome;

```

## Run the Project
### 1. Build the project
To build the project, run the following command.
```bash
npm run build
```

### 2. Generate Key

This section is only needed If the project is cloned from github.

```bash
php artisan key:generate
```

### 3. Run the project
To run the project, run the following command.
```bash
php artisan serve
```

Visit http://localhost:8000 in your browser to see the Laravel application with the integrated Syncfusion EJ2 React Rich Text Editor.
