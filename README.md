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

#### 1. Add firebase & [angularfire2](https://github.com/angular/angularfire) dependencies
```
npm install firebase @angular/fire@7.2
```

#### 2. Create core & shared modules

Core module - to host our services. (Don't forget to add the module to the app using --module=app)
```
ng g m core --module=app
```
Shared module - to keep the imported components & modules. (just following goo practice)
```
ng g m shared --module=app
```

#### 3. Add auth service
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