# How do you transition between two states:
```
  animations: [
    trigger('heroState', [
      state('inactive', style({
        backgroundColor: '#eee',
        transform: 'scale(1)'
      })),
      state('active',   style({
        backgroundColor: '#cfd8dc',
        transform: 'scale(1.1)'
      })),
      transition('inactive => active', animate('100ms ease-in')),
      transition('active => inactive', animate('100ms ease-out'))
    ])
  ]
  ```
# How do you define a wildcard state?
```
* => *
* => active
```

# What does this line do:

```ts
@HostBinding('class.valid') isValid;
```

Binds a host element property (here, the CSS class valid) to a directive/component property (isValid).

# What would be a good use for NgZone service?

The most common use of this service is to optimize performance when starting a work consisting of one or more asynchronous tasks that don't require UI updates or error handling to be handled by Angular. Such tasks can be kicked off via runOutsideAngular and if needed, these tasks can reenter the Angular zone via run.

# Why would you use renderer methods instead of using native element methods?

You are not sure what the context you are doing the rendering. You might be assuming the browser compilation and native DOM methods to be available but that might not be the case. It is better to be safe and let Angular handle the manupulation for elements.
The Renderer is a class that is a partial abstraction over the DOM. Using the Renderer for manipulating the DOM doesn't break server-side rendering or Web Workers (where direct access to the DOM would break).

ElementRef is a class that can hold a reference to a DOM element. This is again an abstraction to not break in environments where the browsers DOM isn't actually available.
Permitting direct access to the DOM can make your application more vulnerable to XSS attacks. Carefully review any use of ElementRef in your code. For more detail, see the Security Guide."

"Use this API as the last resort when direct access to DOM is needed. Use templating and data-binding provided by Angular instead. Alternatively you take a look at Renderer which provides API that can safely be used even when direct access to native elements is not supported."

# What is a good use case for ngrx/store?

Here is a great talk that goes into detail of the problems ngrx solving to manage state in applications by [Victor Savkin](https://twitter.com/victorsavkin?ref_src=twsrc%5Egoogle%7Ctwcamp%5Eserp%7Ctwgr%5Eauthor): https://www.youtube.com/watch?v=brCGZ8Lk-HY&t=1245s

# Can you talk about a bug related to a race condition, how to solve it and how to test it?

You can find the answer of this question in detail in this article: https://blog.nrwl.io/rxjs-advanced-techniques-testing-race-conditions-using-rxjs-marbles-53e7e789fba5

# What is the minimum definition of a component?
Component decorator allows you to mark a class as an Angular component and provide additional metadata that determines how the component should be processed, instantiated and used at runtime.

Components are the most basic building block of an UI in an Angular application. An Angular application is a tree of Angular components. Angular components are a subset of directives. Unlike directives, components always have a template and only one component can be instantiated per an element in a template.

# What is the difference between a component and a directive?

Component will have the template but directive wont. 
Basically there are three types of directives in angular2 according to documentation.

     Component
    Structural directives
    Attribute directives
* Component

is also a type of directive with template,styles and logic part which is most famous type of directive among all in angular2. In this type of directive you can use other directives whether it is custom or builtin in the @component annotation 

* Structural directives

like *ngFor and *ngIf used for changes the DOM layout by adding and removing DOM elements. explained here

* Attribute directives

are used to give custom behaviour or style to the existing elements by applying some functions/logics. like ngStyle is a attribute directive to give style dynamically to the elements. we can create our own directive and use this as Attribute of some predefined or custom elements

# How do components communicate with each other?

    1)Using @Input, @Output and EventEmitter
    
    2)Using Services and injecting them
# How do you create two way data binding in Angular?
    1) By using both Property binding and Event Binding both together at a time.
    2) By using [(ngModel)]     

# What does a lean component mean to you?

ased on the Angular Overview on application architecture, a component should be lean, and contain only the logic to control a view. It should not fetch data from the server, or validate user input, but should delegate any such task to a service.

A component's job is to enable the user experience and nothing more. It mediates between the view (rendered by the template) and the application logic (which often includes some notion of a model). A good component presents properties and methods for data binding. It delegates everything nontrivial to services.
A service, on the other hand, is a specific piece of logic that can be reused multiple times throughout your application. It helps keep your components lean, and your application DRY.

Service is a broad category encompassing any value, function, or feature that your application needs.

Almost anything can be a service. A service is typically a class with a narrow, well-defined purpose. It should do something specific and do it well.

# What would you consider a thing you should be careful doing on ngOnInit()?
Implement this interface to execute custom initialization logic after your directive's data-bound properties have been initialized. ngOnInit is called right after the directive's data-bound properties have been checked for the first time, and before any of its children have been checked. It is invoked only once when the directive is instantiated.
ngOnInit is a life cycle hook called by Angular2 to indicate that Angular is done creating the component.
# What is the differance between ngOnInit() and class constructor?
Constructor : constructor is a default method runs (by deafult) when component is being constructed. When you create an instance of a class that time also constructor(default method) would be called. So in other words, when component is being constructed or/and an instance is  created constructor(default method) is called and relevant code written within is called. Basically and generally in Angular2 it used to inject things like services when component is being constructed for the further use.

OnInit: ngOnInit is component's life cycle hook which runs first after constructor(default method) when component is being initialized.

# What is the purpose of NgModule?

NgModule helps us to organize our components, directives and services into a logical unit, each focused on a feature.

For example, we have 5 components in your project and that each component is dependent on other component or services or pipes then we need to import them into the respective component. And, then repeat the same process for all other components. This will become cumbersome to keep including on each of these components. This is where NgModules recuse us by importing everything to @NgModule which will be available throughout the components under one module.

# How do you decide to create a new NgModule?

When we are dealing with medium or large apps, it includes discrete set of functionality. Administration, Dashboard, Bookings/Orders, Promotions are all examples of areas of our apps that, when linked together, make our app. We basically breakdown our app into smaller pieces called Features / Modules.

In the process of developing an app we might create a feature which we don't want to expose or create a feature which we want to lazy loading when the user decides it is time to revisit the feature. NgModules helps us to separate our features to logical units and load it when required.

# What are the attributes that you can define in an NgModule annotation?
Declare which components, directives, and pipes belong to the module.
Make some of those classes public so that other component templates can use them.
Import other modules with the components, directives, and pipes needed by the components in this module.
Provide services at the application level that any application component can use.
The metadata imports a single helper module, BrowserModule, which every browser app must import.

BrowserModule registers critical application service providers. It also includes common directives like NgIf and NgFor, which become immediately visible and usable in any of this module's component templates.

The declarations list identifies the application's only component, the root component, the top of the app's rather bare component tree.

# what is Compile ahead-of-time (AOT)? differance between it and JIT?

Consider the static alternative which can produce a much smaller application that launches faster, especially on mobile devices and high latency networks.

In the static option, the Angular compiler runs ahead of time as part of the build process, producing a collection of class factories in their own files. Among them is the AppModuleNgFactory.

The syntax for bootstrapping the pre-compiled AppModuleNgFactory is similar to the dynamic version that bootstraps the AppModule class.
* Compile just-in-time (JIT)

In the first, dynamic option, the Angular compiler compiles the application in the browser and then launches the app.

# What is the difference between a module's forRoot() and forChild() and forFeature()
 methods and why do you need it?
* forRoot creates a module that contains all the directives, the given routes, and the router service itself.
* forChild creates a module that contains all the directives and the given routes, but does not include the router service.

RouterModule also offers a forChild static method for configuring the routes of lazy-loaded modules.

forRoot and forChild are conventional names for methods that configure services in root and feature modules respectively.

Angular doesn't recognize these names but Angular developers do. Follow this convention when you write similar modules with configurable service providers.

# What would you have in a shared module?

Create a SharedModule with the components, directives, and pipes that you use everywhere in your app. This module should consist entirely of declarations, most of them exported.

The SharedModule may re-export other widget modules, such as CommonModule, FormsModule, and modules with the UI controls that you use most widely.

The SharedModule should not have providers for reasons explained previously. Nor should any of its imported or re-exported modules have providers. If you deviate from this guideline, know what you're doing and why.

Import the SharedModule in your feature modules, both those loaded when the app starts and those you lazy load later.

# What would you not put shared module?====>providers
This question is addressed in the Why UserService isn't shared section of the NgModules page, which discusses the importance of keeping providers out of the SharedModule.

Suppose the UserService was listed in the module's providers (which it isn't). Suppose every module imports this SharedModule (which they all do).

When the app starts, Angular eagerly loads the AppModule and the ContactModule.

Both instances of the imported SharedModule would provide the UserService. Angular registers one of them in the root app injector (see What if I import the same module twice?). Then some component injects UserService, Angular finds it in the app root injector, and delivers the app-wide singleton UserService. No problem.

Now consider the HeroModule which is lazy loaded.

When the router lazy loads the HeroModule, it creates a child injector and registers the UserService provider with that child injector. The child injector is not the root injector.

When Angular creates a lazy HeroComponent, it must inject a UserService. This time it finds a UserService provider in the lazy module's child injector and creates a new instance of the UserService. This is an entirely different UserService instance than the app-wide singleton version that Angular injected in one of the eagerly loaded components.

# What module would you put a singleton service whose instance will be shared throughout the application (e.g. ExceptionService andLoggerService)?
* CoreModule

Create a CoreModule with providers for the singleton services you load when the application starts.

Import CoreModule in the root AppModule only. Never import CoreModule in any other module.

Consider making CoreModule a pure services module with no declarations

# What is the purpose of exports in a NgModule?
	
The confusion comes from the fact both Angular and ES6 are using the same terminology...

In ES6/TypeScript:

A module is any code file in your project.
An import is a line starting with the import keyword.
An export is a line starting with the export keyword.
In Angular:

A module is a class decorated with @NgModule. It serves as a registry (aka container) for all the components, pipes, directives and providers in your application.
An import is what you put in the imports property of the @NgModule decorator. It enables an Angular module to use functionality that was defined in another Angular module.
An export what you put is the exports property of the @NgModule decorator. It enables an Angular module to expose some of its components/directives/pipes to the other modules in the applications. Without it, the components/directives/pipes defined in a module could only be used in that module.
ES6 modules/imports/exports are very low-level. They are a feature of the ES6 language, just like keywords like const or let... In ES6/TypeScript, each file has ITS OWN SCOPE. So whenever you need to use a class/function/variable in a file and that class/function/variable was defined in another file, you must import it (the counterpart being that it must be exported in the file where it was defined). This is not specific to Angular. ALL PROJECTS WRITTEN IN ES6 can use modules/imports/exports in this manner.

On the other hand, Angular's modules/imports/exports are a feature of the Angular framework. They only make sense in Angular world. Other JavaScript frameworks might have similar notions but they'll use a different syntax.

# What is a pure pipe?
A pipe takes in data as input and transforms it to a desired output
# What is an async pipe?
The AsyncPipe accepts a Promise or Observable as input and subscribes to the input automatically, eventually returning the emitted values.

The AsyncPipe is also stateful. The pipe maintains a subscription to the input Observable and keeps delivering values from that Observable as they arrive.
# How do you create a custom pipe?
```
import { Pipe, PipeTransform } from '@angular/core';
/*
 * Raise the value exponentially
 * Takes an exponent argument that defaults to 1.
 * Usage:
 *   value | exponentialStrength:exponent
 * Example:
 *   {{ 2 | exponentialStrength:10 }}
 *   formats to: 1024
*/
@Pipe({name: 'exponentialStrength'})
export class ExponentialStrengthPipe implements PipeTransform {
  transform(value: number, exponent: string): number {
    let exp = parseFloat(exponent);
    return Math.pow(value, isNaN(exp) ? 1 : exp);
  }
}
```
# How does async pipe prevents memory leeks?

Async pipe knows about the lifespan of the component and unscubscribes from the observable if necessary.


