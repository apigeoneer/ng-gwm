# NgGwm

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 13.2.4.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.

# ng-gwm

#### 1. Add necessary dependencies, modules & services

* Add firebase & [angularfire2](https://github.com/angular/angularfire) dependencies
```
npm install firebase @angular/fire
```

* Create core & shared modules

Core module - to host our services. (Don't forget to add the module to the app using --module=app)
```
ng g m core --module=app
```
Shared module - to keep the imported components & modules. (just following goo practice)
```
ng g m shared --module=app
```

* Add auth service
Create a service for authentication & add it to the core module.
```
ng g s core/auth
```

```
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { AuthService } from './auth.service';

@NgModule({
  declarations: [],
  imports: [
    CommonModule
  ],
  providers: [AuthService]
})
export class CoreModule { }
```

#### 2. Set up Firebase
* Create a project in Firebase.
* Choose the web (</>) option.
* Copy the forebaseConfig object & paste it in the environments.ts file in your project.
```
export const environment = {
  production: false,
  firebase: {
    apiKey: "AIzaSyAPJjQzfZb_06TTGOv85rpJl9zIkXo5rjE",
    authDomain: "ng-gwm.firebaseapp.com",
    projectId: "ng-gwm",
    storageBucket: "ng-gwm.appspot.com",
    messagingSenderId: "837072589476",
    appId: "1:837072589476:web:b3c3aeabebdb81d9ec4c31",
    measurementId: "G-85RXTRGSBT"
  }
};
```
* Import necessary angular file modules & also the environment.
```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { provideFirebaseApp, getApp, initializeApp } from '@angular/fire/app';
import { getFirestore, provideFirestore } from '@angular/fire/firestore';
import { getStorage, provideStorage } from '@angular/fire/storage';
import { getAuth, provideAuth } from '@angular/fire/auth';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { CoreModule } from './core/core.module';
import { SharedModule } from './shared/shared.module';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    provideFirebaseApp(() => initializeApp({ ... })),
    provideFirestore(() => getFirestore()),
    provideStorage(() => getStorage()),
    provideAuth(() => getAuth()),
    CoreModule,
    SharedModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

