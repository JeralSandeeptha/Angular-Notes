# Angular

## Table of Contents

- [Prerequisites](#prerequisites)
- [Get Started](#get-started)
- [Create Project](#create-project)
- [Folder Structure](#folder-structure)
- [Angular Components](#angular-components)
- [Data Binding](#data-binding)
- [Template Variables](#angular-components)
- [Directives](#directives)
- [Forms](#forms)
- [Services](#services)
- [Interceptors](#interceptors)

---

## Prerequisites

For work with the angular first we need to have Nodejs install in your computer
[Download Nodejs](https://nodejs.org/en)

---

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

---

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

---

## Folder Structure

- node_modules - holds all the dependencies of the project
- public - holds static content of the project
- src - holds the all the code base files related to the project
- package.json - holds all the dependencies for the project
- package-lock.json - holds the logs for the package.json file
- tsconfig files - holds the configurations for the Typescript
- angular.json - holds the configurations for Angular

---

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

---

## Data Binding

Angular Data Binding is 2 types.
- One way data binding
- Two way data binding

### One way data binding 

1. Interpolation
- With this we can use these as variables
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
- We can handle classes of an element with variables.
```html
<button [class.active]="isActive">Click</button>
```
```scss
.active {
  background-color: red;
}
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

  isActive = true;
}
```

3. Property Binding
- We can handle properties of an element with variables.
```html
<img [src]="imageLink" alt="image">
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

  imageLink = 'https://hips.hearstapps.com/hmg-prod/images/little-cute-maltipoo-puppy-royalty-free-image-1652926025.jpg?crop=0.444xw:1.00xh;0.129xw,0&resize=980:*';
  
}
```

4. Style Binding
- We can dynamically change the styles
```html
<h1 [style.font-size]="fontSize">Hello Jeral Sandeeptha</h1>
```
```scss
.active {
  background-color: red;
}
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

  fontSize = '50px';
}
```

5. Attribute Binding
```html
<button [attr.role]="task">Click</button>
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

  task = 'role';

}
```

5. Event Binding
- We can attach js functions to the HTML
```html
<button (click)="handleClick()">Click</button>
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

  handleClick() {
    console.log('Hello');
  }
}
```

### Two way data binding

```html
<h1>{{ name }}</h1>
<input type="text" [(ngModel)]="name">  <!-- Correct syntax -->
```
```js
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms'; // Import FormsModule correctly
import { RouterOutlet } from '@angular/router';

@Component({
  selector: 'app-root',
  standalone: true, // Required for standalone components
  imports: [RouterOutlet, FormsModule], // Ensure FormsModule is imported
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent {
  name: string = ''; // Define name property
}
```

---

## Template Variables

We can attach a variable to the a html template.
Then we can use that variable for access different variables.
```html
<input type="text" #inputVariable>
<button (click)="handleClick(inputVariable.value)" >Submit</button>
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

  handleClick(value: any) {
    console.log(value);
  }
}
```

## Directives

## Forms