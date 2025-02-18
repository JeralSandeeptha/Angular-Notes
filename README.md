# Angular

## Table of Contents

- [Prerequisites](#prerequisites)
- [Get Started](#get-started)
- [Create Project](#create-project)
- [Folder Structure](#folder-structure)
- [Angular Components](#angular-components)
- [Data Binding](#data-binding)

---

## Prerequisites

For work with the angular first we need to have Nodejs install in your computer

## Get Started

To get started project we need to install Angular CLI because we can create a angular project with this
[Angular CLI](https://github.com/angular/angular-cli)

For install the Angular CLI,

```bash
npm install -g @angular/cli
```

To see the angular cli version

```bash
ng version
```

For more information on using the Angular CLI, including detailed command references, visit the [Angular CLI Overview and Command Reference](https://angular.dev/tools/cli) page

## Create Project

To create a new project

```bash
ng new MyProject
```

After that we need to add node modules

```bash
npm install
```

To start a local development server, run:
```bash
ng serve
```

If you want to see the dev app within your mobile.
```bash
ng serve --host 192.168.1.138
```

To access the web application got to the following url
```bash
http://localhost:4200/
```

If you are using powershell sometimes we need to allow some policies. If not use different CLI.

## Folder Structure

- node_modules - holds all the dependencies of the project
- public - holds static content of the project
- src - holds the all the code base files related to the project
- package.json - holds all the dependencies for the project
- package-lock.json - holds the logs for the package.json file
- tsconfig files - holds the configurations for the Typescript
- angular.json - holds the configurations for Angular

## Angular Components

Components are pieces of the UI
Component has 4 files
- .component.ts - handle typescript
- .component.scss - handle stylings
- .component.html - handle html
- .component.test.ts - handle testing

We can create a component files with CLI
```bash
ng g c navbar
```

This will generate 4 files regarding to the component.

```js
//navbar.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-navbar',
  imports: [],
  templateUrl: './navbar.component.html',
  styleUrl: './navbar.component.scss'
})
export class NavbarComponent {

}
```

This is a basic component.

## Data Binding

Angular Data Binding is 2 types.

### One way data binding 

1. Interpolation
With this we can bind 
```html
<h1>My name is {{ name }} </h1>
```
```js
import { Component } from '@angular/core';
import { RouterOutlet } from '@angular/router';

@Component({
  selector: 'app-root',
  imports: [RouterOutlet],
  templateUrl: './app.component.html',
  styleUrl: './app.component.scss'
})
export class AppComponent {
  name = 'Jeral Sandeeptha';
}
```

2. Class Binding

3. Attribute Binding

4. Style Binding

### Two way data binding

