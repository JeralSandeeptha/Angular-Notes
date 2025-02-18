# Angular

## Table of Contents

- [Prerequisites](#prerequisites)
- [Get Started](#get-started)
- [Create Project](#create-project)
- [Folder Structure](#folder-structure)
- [Angular Components](#angular-components)
- [Data Binding](#data-binding)
- [Template Variables](#angular-components)
- [Routing](#routing)
- [Components Relationships](#components-relationships)
- [Directives](#directives)
- [Pipes](#pipes)
- [Services](#services)
- [Forms](#forms)
- [Interceptors](#interceptors)
- [Feature Modules](#feature-modules)
- [State Management](#state-management)
- [Testing](#testing)

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

---

## Routing

Main routing file is app.route.ts file. We defined all the routes in here.

We should import related router modules.

```js
import { Routes } from '@angular/router';
import { HomeComponent } from './components/home/home.component';
import { AboutComponent } from './components/about/about.component';
import { ContactComponent } from './components/contact/contact.component';
import { NotfoundComponent } from './components/notfound/notfound.component';

export const routes: Routes = [
  // first one is to redirect
  { path: '', redirectTo: '/home', pathMatch: 'full' },
  // Basic pages
  { path: 'home', component: HomeComponent },
  { path: 'about', component: AboutComponent },
  { path: 'contact', component: ContactComponent },
  // This is for not found page should be in the last
  { path: '**', component: NotfoundComponent },
];
```
```html
<!-- routerLinkActive for active class -->
<ul>
  <li>
    <a routerLinkActive="active" routerLink="/home">Home</a>
    <a routerLinkActive="active" routerLink="/contact">contact</a>
    <a routerLinkActive="active" routerLink="/about">About</a>
  </li>
</ul>
<router-outlet />
```
```scss
ul {
  list-style: none;

  li {
    display: inline-block;
    padding: 8px 15px;
    border: 1px solid red;
    cursor: pointer;

    a {
      text-decoration: none;
    }
  }
}

.active {
  color: black;
  background-color: red;
}
```

---

## Components Relationships

We can pass the data through components.

From this concept we can create reusbale components.

For that we can use two things.
- Parent To Child 
- Child To Parent

1. Parent to Child data passing
For this we should use @Input Decorator

I have App component. Wanted to pass user data to user component.

This is the user type.
```js
interface User{
  fname: string,
  lname: string,
  mobile: string,
  nic: string,
}
```

```js
import { Component } from '@angular/core';
import { RouterOutlet } from '@angular/router';
import { UserComponent } from "./components/user/user.component";
import { User } from './types/types';

@Component({
  selector: 'app-root',
  imports: [RouterOutlet, UserComponent],
  templateUrl: './app.component.html',
  styleUrl: './app.component.scss'
})
export class AppComponent {

  user: User = {
    fname: 'Yohan',
    lname: 'Sandeepa',
    mobile: '0778250712',
    nic: '200015003010'
  }

}
```
```html
<app-user [user]="user"/>
```

```js
import { Component, Input } from '@angular/core';
import { User } from '../../types/types';

@Component({
  selector: 'app-user',
  imports: [],
  templateUrl: './user.component.html',
  styleUrl: './user.component.scss'
})
export class UserComponent {

  @Input() user: User = {
    fname: '',
    lname: '',
    nic: '',
    mobile: ''
  };
}
```
```html
<h1>{{ user.fname }} {{ user.lname }}</h1>
<h1>{{ user.nic }}</h1>
<h1>{{ user.mobile }}</h1>
```

2. Child to Parent data passing
For this we should use @Output Decorator

---

## Directives

---

## Forms

---