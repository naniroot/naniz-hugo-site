---
title: "Model View Controller (MVC) Best Practices"
date: 2019-03-23T09:22:53-07:00
draft: false
images:
tags: [model, view, controller, mvc, programming, abstract]
---

If you have ever taken a web framework tutorial like Django, Rails etc, one of the first things they introduce is the Model-View-Controller pattern. This is a very simple pattern to organize your web service and distribute responsibilities for readability and maintainability. Since many (Service Oriented Architecture) SOA frameworks have similar constructs, this pattern is used widely. Exceptions of this pattern could be found in dequeuer services that generally don't have endpoints to be invoked.

Here is a simple diagram explaining this pattern,

{{< image src="/images/mvc_schematic.png" alt="MVC Schematic" position="center">}}

What I want to do with this article is to cement the objectives of each component- model, view and controller. I am hoping at the end of this you will understand why we structure our services in a certain way and its advantages. 

### Main Objectives of each component

- **Model** - Reusability
- **View** - Readability
- **Controller** - Testability

## MODEL

### Main objective - Reusability

Model could be DAOs or service clients. It is the component that goes out of the service to get the data needed to do your business logic. It should be designed such that it can be passed and used by any controller without any modification.

The model

- Should have its own **execution context or thread pool**.
- Should specify number of connections to use, so that the total connections opened is constant across all controllers.
- Should set the timeout to the requests.
- Should be **agnostic** to the controller using it.
- Should handle exceptions, 400s, timeouts etc and wrap them in service exceptions to pass back to the controllers.
- Should **NOT have any business logic** as reusability is key.

It's important to wrap client exceptions with service exceptions, this allows controller to not worry about the zillion different exceptions throw by clients and can only worry about the business logic. Once the model is written and has tests, they can be reused among any number of controllers.

## VIEW

### Main Objective - Readability

View also known as resource or REST specification is the contract that the service has with its clients. It specifies what input it takes and what output it generates for the input. Your clients don't care how you achieve the response, they only care about the response. Keep this as simple as possible, so clients know exactly what to expect when integrating with your service.

The view

- Should have its own **execution context or thread pool**.
- Should specify the input (path param, query param, request type like GET, POST etc).
- Should do validation on input and throw 400s.
- Should NOT handle things like timeout for the clients.
- Should **NOT have any business logic**.
- It's recommended to specify the view using open API specification [https://swagger.io/specification/](https://swagger.io/specification/) so that code generation tools can be used to generate the client and tests.

## Controller

### Main Objective - Testability

Controller (sometimes known as manager) is the core of your service. It is responsible for the business logic and should do all the heavy lifting. It will take the validated input from the resource/view, call the necessary model/client to get additional data, process it and send the output back to the view.

General rule of thumb, a resource can call any controller, a controller can call any of the model/clients to get its data. This makes it easy to test as all the business logic will reside in the controller.

Since controller does the business logic in your service, it should be covered by comprehensive tests.

- Should have its own **execution context or thread pool**.
- Should have extensive tests to cover your business logic.
- Should depend only on MODELs to get its data, not other controllers.
- Should NOT call other controllers
- Can have until/helper classes to [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) up the processing but those util classes should not use any of the model/client classes or respond back to views.


