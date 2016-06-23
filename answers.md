# ngExam Answers


* What's MVC architecture?
    * Model-View-Controller is a software architectural pattern for implementing user interfaces on computers. It divides a given software application into three interconnected parts, in order to separate internal representations of information from the ways that information is presented to or accepted from the user.
    * Model: directly manages the data, logic, and rules of the application.
    * View: can be any output representation of information, such as a chart or a diagram. Multiple views of the same information are possible, such as a bar chart for management and a tabular view for accountants.
    * Controller: accepts input and converts it to commands for the model or view.
* What's MVVM architecture?
    * Model-View-Viewmodel is a software architectural pattern that facilitates separation of development of the graphical user interface from development of business logic or back-end logic.
    * Model: refers either to a domain model, which represents real state content (an object-oriented approach), or to the data access layer, which represents content (a data-centric approach).
    * View: can be any output representation of information, such as a chart or a diagram. Multiple views of the same information are possible, such as a bar chart for management and a tabular view for accountants.
    * Viewmodel: an abstraction of the view exposing public properties and commands. Instead of the controller of the MVC pattern, or the presenter of the MVP pattern, MVVM has a binder. In the view model, the binder mediates communication between the view and the data binder. The view model has been described as a state of the data in the model.
* What's two way binding?
    * Data-binding in Angular apps is the automatic synchronization of data between the model and view components. The view is a projection of the model at all times. When the model changes, the view reflects the change, and vice versa.
    * First the template (which is the uncompiled HTML along with any additional markup or directives) is compiled on the browser. The compilation step produces a live view. Any changes to the view are immediately reflected in the model, and any changes in the model are propagated to the view.
* What's ng-model?
    * The ngModel directive binds an input,select, textarea (or custom form control) to a property on the scope.
* What is `$http`?
    * The $http service is a core Angular service that facilitates communication with the remote HTTP servers via the browser's XMLHttpRequest object or via JSONP.
* What is ng-repeat?
    * The ngRepeat directive instantiates a template once per item from a collection. Each template instance gets its own scope.
* What are `$index`, `$even`, `$odd`, `$first`, and `$last`?
    * Special properties exposed on the local scope of each ngRepeat template instance.
    * $index: number, iterator offset of the repeated element (0..length-1).
    * $even: boolean, true if the iterator position $index is even (otherwise false).
    * $odd: boolean, true if the iterator position $index is odd (otherwise false).
    * $first: boolean, true if the repeated element is first in the iterator.
    * $middle: boolean, true if the repeated element is between the first and last in the iterator.
    * $last: boolean, true if the repeated element is last in the iterator.
* How would you filter a list via ng-repeat?
    * A filter can be applied to a list rendered by ngRepeat using the pipe character followed by the filter and any necessary arguments to pass into the filter.
    * Example: `item in items | filter:searchText track by item.id` is a pattern that might be used to apply a filter to items in conjunction with a tracking expression.
* What's the difference between `angular.module('app' , [])` and `angular.module('app')`
    * Providing a second argument of `[]` to `angular.module()` will attempt to create a new angular module to be named `app`.
    * The latter statement will attempt to obtain a reference to an already-existent angular module named `app`.
* What are directives (briefly)?
    * Markers on a DOM element (such as an attribute, element name, comment or CSS class) that tell AngularJS's HTML compiler (`$compile`) to attach a specified behavior to that DOM element (e.g. via event listeners), or even to transform the DOM element and its children.
* Why would you use ng-submit instead of ng-click in some cases?
    * ngSubmit is more likely to be used for form submission than ngClick.
    * ngSubmit enables binding angular expressions to onsubmit events.
    * Additionally it prevents the default action (which for form means sending the request to the server and reloading the current page), but only if the form does not contain `action`, `data-action`, or `x-action` attributes.
* What's Dependency Injection?
    * Dependency Injection (DI) is a software design pattern that deals with how components get hold of their dependencies.
    * The Angular injector subsystem is in charge of creating components, resolving their dependencies, and providing them to other components as requested.
* Do other frameworks use dependency injection (even if only for internal use)?
    * yes (React,Ember)
* How would you inject services and what are the different ways to do so?
    * Angular invokes certain functions (like service factories and controllers) via the injector. You need to annotate these functions so that the injector knows what services to inject into the function.
    * Inline Array Notation: This is the preferred way to annotate application components.
    ```
        someModule.controller('MyController', ['$scope', 'greeter', function($scope, greeter) {}]);
    ```
    * `$inject` Property Annotation: o allow the minifiers to rename the function parameters and still be able to inject the right services, the function needs to be annotated with the `$inject` property. The `$inject property is an array of service names to inject.
    ```
        var MyController = function($scope, greeter) {
          // ...
        }
        MyController.$inject = ['$scope', 'greeter'];
        someModule.controller('MyController', MyController);
    ```
    * Implicit Annotation: The simplest way to get hold of the dependencies is to assume that the function parameter names are the names of the dependencies. This method will not work with JavaScript minifiers/obfuscators because of how they rename parameters.
    ```
        someModule.controller('MyController', function($scope, greeter) {});
    ```
* What's jqLite?
    * jqLite is a tiny, API-compatible subset of jQuery that allows Angular to manipulate the DOM in a cross-browser compatible way. jqLite implements only the most commonly needed functionality with the goal of having a very small footprint.
    * If jQuery is available, `angular.element` is an alias for the jQuery function. If jQuery is not available, `angular.element` delegates to Angular's built-in subset of jQuery, called "jQuery lite" or jqLite.
* How do you ensure Angular uses jQuery when including them both?
    * To use `jQuery`, simply ensure it is loaded before the `angular.js` file. You can also use the `ngJq` directive to specify that jqlite should be used over jQuery, or to use a specific version of jQuery if multiple versions exist on the page.
* What are promises and how would you use them?
    * The Promise object is used for asynchronous computations. A Promise represents an operation that hasn't completed yet, but is expected in the future.
    * Can be used with angular's `$q` service, an implementation of promises/deferred objects inspired by Kris Kowal's Q.
        * A service that helps you run functions asynchronously, and use their return values (or exceptions) when they are done processing.
* What's the difference between factory/provider/service/value/constant?
    * All are specialized objects conform to a specific Angular framework API. These objects are one of controllers, directives, filters or animations. Instantiated and wired together by angular's injector service. The recipes for creating factory/service/value/constant are based on the recipe for creating a provider.
    * can have dependencies: factory, service, provider
    * uses type friendly injection: service, value, constant
    * object available in config phase: constant, provider
    * can create functions: all
    * can create primitives: factory, constant, value, provider
* When would you use each one?
    * Service: works better for objects of a custom type. A service is a singleton and will only be created once by AngularJS
    * Factory: A factory is a lot like a service in the sense that it is a singleton and dependencies can be specified in the function. The difference between a factory and a service is that a factory injects a plain function so AngularJS will call the function and a service injects a constructor.
    * Provider: should be used when creating reusable code that needs global configuration.
    * Constant: A constant can be injected everywhere. A constant can not be intercepted by a decorator, that means that the value of a constant should never be changed.
    * Value: A value is nothing more than a simple injectable value. The value can be a string, number but also a function. Value differs from constant in that value can not be injected into configurations, but it can be intercepted by decorators.
* What are filters?
    * A filter formats the value of an expression for display to the user. They can be used in view templates, controllers or services and it is easy to define your own filter.
* Why would you use ng-src, ng-bind, and ng-cloak?
    * ngSrc: necessary when attempting to interpolate an angular expression such as `{{ expression }}` inside of an html element's `src` attribute.
    * ngBind: The `ngBind` attribute tells Angular to replace the text content of the specified HTML element with the value of a given expression, and to update the text content when the value of that expression changes.
        * It is preferable to use `ngBind` instead of `{{ expression }}` if a template is momentarily displayed by the browser in its raw state before Angular compiles it. Since `ngBind` is an element attribute, it makes the bindings invisible to the user while the page is loading.
    * ngCloak: The `ngCloak` directive is used to prevent the Angular html template from being briefly displayed by the browser in its raw (uncompiled) form while your application is loading. Use this directive to avoid the undesirable flicker effect caused by the html template display.
* What's the difference between ng-if and ng-show?
    * ngIf will remove the element from the DOM when false. ngShow will hide the element using the `.ng-hide` CSS class when false, but the element will remain in the DOM.
* What phases are there in angular?
    * config -> bootstrap -> run
* Why would you use `.config()` and `.run()` phase?
    * Configuration blocks: get executed during the provider registrations and configuration phase, can be used to provide custom application configuration before running the application.
    * Run blocks: get executed after the injector is created and are used to kickstart the application. Run blocks are the closest thing in Angular to the main method. Can be used to execute code that needs to be run in order to start the application.
* What is ng-app and how does angular bootstrap?
    * Directive used to auto-bootstrap an angular application. The `ngApp` directive designates the root element of the application and is typically placed near the root element of the page.
    * Angular initializes automatically upon DOMContentLoaded event or when the angular.js script is evaluated if at that time document.readyState is set to 'complete'. At this point Angular looks for the ngApp directive which designates your application root. If the ngApp directive is found then Angular will:
        * load the module associated with the directive.
        * create the application injector.
        * compile the DOM treating the `ngApp` directive as the root of the compilation. This allows you to tell it to treat only a portion of the DOM as an Angular application.
* When would you use `$q.all()`?
    * If it is necessary to combine multiple promises into a single promise that should not be resolved until all of the input promises are resolved.
* Where would you make your network calls controller, template, directive, or service and why? (where would you use $http)
    * Best practice is to create a service that returns a promise to the returned data, then call that in your controller and handle the promise there to populate your $scope property.
    ```
        module.factory('angularService', function($http) {
            return {
                getData: function() {
                    // return promise directly
                    return $http.get('/url')
                        .then(function(result) {
                            // resolve promise as data
                            return result.data;
                        });
                }
            }
        });
    ```
    ```
        module.controller('angularController', function($scope, angularService) {
            angularService.getData().then(data) {
                $scope.data = data;
            });
        });
    ```
* Say that you are going to alert an error where would you put that alert from a network call? Service, controller, template and why?
    * [Answer](https://gist.github.com/gdi2290/b9d34955f0d3bce2c1b6)
* How would you dynamically filter a list with an ng-repeat? (clicking on different filters)
    * create a custom filter
* What's ng-messages and ng-message?
    * `ngMessages` is a directive that is designed to show and hide messages based on the state of a key/value object that it listens on. The directive itself complements error message reporting with the ngModel $error object (which stores a key/value state of validation errors).
    * `ngMessage` is a directive with the purpose to show and hide a particular message. For `ngMessage` to operate, a parent `ngMessages` directive on a parent DOM element must be situated since it determines which messages are visible based on the state of the provided key/value map that `ngMessages` listens on.
* What's ng-style and ng-class?
    * The `ngStyle` directive allows you to set CSS style on an HTML element conditionally.
    * The `ngClass` directive allows you to dynamically set CSS classes on an HTML element by databinding an expression that represents all classes to be added.
        * If the expression evaluates to a string, the string should be one or more space-delimited class names.
        * If the expression evaluates to an object, then for each key-value pair of the object with a truthy value the corresponding key is used as a class name.
        * If the expression evaluates to an array, each element of the array should either be a string as in type 1 or an object as in type 2. This means that you can mix strings and objects together in an array to give you more control over what CSS classes appear. See the code below for an example of this.
* How would you attach something to the header of every http call?
    * The default HTTP headers can be fully configured by accessing the `$httpProvider.defaults.headers` configuration object. To add or overwrite the default HTTP headers for all http requests, add or remove a property from the `$httpProvider.defaults.headers.common` configuration object.
    * The defaults can also be set at runtime via the `$http.defaults` object in the same fashion.
    ```
        module.run(function($http) {
            $http.defaults.headers.common.Authorization = 'Basic GsWelF53x';
        });
    ```
* What is `$scope.$on()` and how would you use it?
    * Listens on events of a given type.
    ```
        module.controller('parentController1',function($scope) {
            $scope.$broadcast('event1', 'data');
        });
    ```
    ```
        module.controller('childController1', function($scope) {
            $scope.$on('event1', function(event, data) {
                console.log(data);
            });
        });
    ```
    ```
        module.controller('parentController2', function($scope) {
            $scope.$on('event2', function(event, data) {
                console.log(data);
            });
        });
    ```
    ```
        module.controller('childController2', function($scope) {
            $scope.$emit('event', 'data');
        });
    ```
* What are `$http` interceptors?
    * The interceptors are service factories that are registered with the `$httpProvider` by adding them to the `$httpProvider.interceptors` array. The factory is called and injected with dependencies (if specified) and returns the interceptor.
    * `request`: interceptors get called with a http config object.
    * `requestError`: interceptor gets called when a previous interceptor threw an error or resolved with a rejection.
    * `response`: interceptors get called with http response object.
    * `responseError`: interceptor gets called when a previous interceptor threw an error or resolved with a rejection.
* What is `"$locationChangeStart"`?
    * The event that is broadcasted before a URL will change.
* What's html5Mode?
    * In HTML5 mode, the $location service getters and setters interact with the browser URL address through the HTML5 history API. This allows for use of regular URL path and search segments, instead of their hashbang equivalents.
* How do you turn off cache for a `$http` call?
    * Set the `cache` boolean value to `false` in the `config` object that is passed to `$http`.
* What is the `$templateCache`?
    * The first time a template is used, it is loaded in the template cache for quick retrieval. You can load templates directly into the cache in a script tag, or by consuming the `$templateCache` service directly.
* How would you implement auth as in locking down certain parts of the app?
    * TODO
* What's ui-router and why use it over ng-route?
    * Angular ui-router is a client-side Single Page Application routing framework for AngularJS. The ui-router supports everything ngRoute is capable of, and supports extra functionality as well.
    * ui-router allows for nested views and multiple named views.
    * ui-router allows for strong-type linking between states based on state names.
    * the concept of the decorator exists within ui-router, allowing routes to be dynamically created based on the URL that is being accessed.
    * states allow mapping and access of different information about different states, information can be passed between states via `$stateParams`.
* What are states?
    * ui-router applications are modeled as a hierarchical tree of states. UI-Router provides a state machine to manage the transitions between those application states in a transaction-like manner.
* How do you resolve resources via state/route and how would you do so?
    * Use resolve to provide your controller with content or data that is custom to the state. resolve is an optional map of dependencies which should be injected into the controller.
    ```
        $stateProvider.state('stateName', {
            resolve: {
                objectName: function() {
                    return { value: 'val' };
                }
            },
            controller: function($scope, objectName) {
                $scope.objectName = objectName.value;
            }
        }
    ```
* Given 3 nested states, how would you load the most nested one after the root state resolves while allowing the middle state to load asynchronously?
    * TODO
* What types of directives are there?
    * `$compile` can match directives based on element names, attributes, class names, as well as comments.
    * Best Practice: Prefer using directives via tag name and attributes over comment and class names. Doing so generally makes it easier to determine what directives a given element matches.
* What is `$scope`?
    * The application object, and the owner of application variables and functions. Angular will invoke the controller with a `$scope` object.
    * Scopes provide separation between the model and the view, via a mechanism for watching the model for changes. They also provide event emission/broadcast and subscription facility.
* What is `$rootScope`?
    * Every application has a single root scope. All other scopes are descendant scopes of the root scope.
* What is `"$destroy"`?
    * Removes the current scope (and all of its children) from the parent scope.
* What's one time binding?
    * An expression that starts with `::` is considered a one-time expression.
    * The main purpose of one-time binding expression is to provide a way to create a binding that gets deregistered and frees up resources once the binding is stabilized. Reducing the number of expressions being watched makes the digest loop faster and allows more information to be displayed at the same time.
* When and where would you normally use `.$watch()`?
    * using `$scope.$watch()` should replace the need for events.
* What's a stateful filter vs a stateless filter?
    * Filters that have dependencies are usually stateful.
    * In a stateless filter, the expression passed into the filter doesn't change, so the result of the expression doesn't change either.
    * The `translate` filter of the angular-translate module is statefu because it relies upon the `$translate` service to return the correct translation.
    * Stateful filters must set their `$stateful` property to `true`.
* What are `.$dirty`, `.$pristine`, `.$valid`, `.$invalid`, and `.$submitted`?
    * Properties of the FormController used to hold form state.
    * `$pristine`: true if user has not interacted with form yet.
    * `$dirty`: true if user has already interacted with form.
    * `$valid`: true if all containing forms and controls are valid.
    * `$invalid`: true if at least one containing control for form is invalid.
    * `$submitted`: true if user has submitted the form even if it's invalid.
* What's NgModelController?
    * NgModelController provides API for the ngModel directive. The controller contains services for data-binding, validation, CSS updates, and value formatting and parsing.
* What's FormController?
    * FormController keeps track of all its controls and nested forms as well as the state of them, such as being valid/invalid or dirty/pristine.
* What's ng-model-options and why would you use it?
    * Allows tuning how model updates are done.
    * Can be used to specify a custom list of events that will trigger a model update.
    * Can be used to specify a debouncing delay so that the actual update does not occur until a timer expires.
* What are `$validators` and `$asyncValidators`?
    * services that can be used to set the validity state of an NgModelController or FormController.
* What's the difference between `scope`, `$scope`, and `$rootScope`?
    * a property assigned with `$scope` cannot be used outside the controller in which it is defined, while a property assigned with `$rootScope` can be used anywhere.
    * Unlike `link` functions, controller functions are called by Angular's dependency injection system. While `scope` of the directive's link function, and `$scope` are both instances of the Scope class, the scope must be referenced using Angular's `$scope` service in controller functions to satisfy dependency injection.
* What's the difference between controller and link directives?
    * link is the function which should be used to attach an event handler or modify the DOM.
    * controller is used to share or reuse `$scope` data, or for directive interaction.
    * As Angular walks the DOM tree, it instantiates the directive controllers on the way down, and links the directives on the way back up.
* How do you require a controller in a directive?
    * Require another directive and inject its controller as the fourth argument to the linking function. The require property can be a string, an array or an object.
* How do you require more than one controller in a directive?
    * use an array containing the names of controllers to pass to the require property of the linking function.
    * use an object whose property values are the names of the controllers to pass to the require property of the linking function.
* What's an isolated scope?
    * the isolate scope of the directive isolates everything except models that you've explicitly added to the scope: {} hash object.
* For an isolate scope what are these symbols `?`,`@`,`=`,`&`,`*` in relation to directives
    * `@`: bind a local scope property to the value of DOM attribute. Result is always a string.
    * '=': set up bidirectional binding between a local scope property and an expression passed via the attribute.
    * '<': set up one-way binding between a local scope property and an expression passed via the attribute.
    * '&': provides a way to execute an expression in the context of the parent scope.
    * TODO `?`, `*` ?
* What are compile/pre-link/post-link phase for directives?
    * compile: traverse the DOM and collect all of the directives. The result is a linking function.
    * pre-link: function executed before the child elements are linked. Not safe to do DOM transformation since the compiler linking function will fail to locate the correct elements for linking.
    * post-link: function executed after the child elements are linked. It is safe to do DOM transformation on elements that are not waiting for their async templates to be resolved.
* What is `$interpolate`?
    * Compiles a string with markup into an interpolation function. This service is used by the HTML $compile service for data binding.
* What is `$compile`?
    * Compiles an HTML string or DOM into a template and produces a template function, which can then be used to link `scope` and the template together.
* What is `$observe`?
    * Observes an interpolated attribute.
    * The observer function will be invoked once during the next `$digest` following compilation. The observer is then invoked whenever the interpolated value changes.
* What's transclusion?
    * Transclusion is the process of extracting a collection of DOM elements from one part of the DOM and copying them to another part of the DOM, while maintaining their connection to the original AngularJS scope from where they were taken.
* Why would you need transclusion?
    * Transclusion is often used to insert the original contents of a directive's element into a specified place in the template of the directive.
    * The benefit is that the transcluded content has access to the properties on the scope from which it was taken, even if the directive has isolated scope.
* What's `bindToController:` and `controllerAs:` syntax?
    * This property is used to bind scope properties directly to the controller. It can be either true or an object hash with the same format as the scope property. Additionally, a controller alias must be set, either by using `controllerAs: 'myAlias'` or by specifying the alias in the controller definition: `controller: 'myCtrl as myAlias'`.
* What are directives and what are components?
    * In Angular, a Component is a special kind of directive that uses a simpler configuration which is suitable for a component-based application structure.
    * All components are directives, but not all directives are components.
* What's the difference between `.$broadcast()`, and `.$emit()`?
    * `$broadcast()` dispatches an event downwards.
    * `$emit()` dispatches an event upwards.
* What are `$timeout()` and `$interval()` and how do you cancel them?
    * `$timeout()`: Angular's wrapper for window.setTimeout. To cancel a timeout request, call `$timeout.cancel(promise)`.
    * `$interval()`: Angular's wrapper for window.setInterval. To cancel an interval, call `$interval.cancel(promise)`.
* What's dirty checking?
    * After evaluating the expression, the `$apply` method performs a `$digest`. In the $digest phase the scope examines all of the `$watch` expressions and compares them with the previous value. This dirty checking is done asynchronously.
    * Dirty checking can be done with three strategies: By reference, by collection contents, and by value.
* Do other frameworks use dirty checking?
    * yes (React,Polymer)
* What is the `.$digest()` loop?
    * The Angular context refers specifically to code that runs inside the Angular event loop, referred to as the `$digest` loop. The `$watch` list and the `$evalAsync` list are the two major components of the `$digest` loop.
* What's the difference between `.$digest()` and `.$apply()`?
    * `$apply()`: starts digestion cycle explicitly. All watchers are checked, the entire application starts the `$digest` loop. calls `$rootScope.$digest()` internally after executing an optional function parameter.
    * `$digest()`: starts digestion cycle with `$digest` method for current scope and its children. Parent scopes will not be checked.
* What are `$watchGroup` and `$watchCollection`?
    * `$watchGroup`: A variant of `$watch()` where it watches an array of watchExpressions. If any one expression in the collection changes the listener is executed.
    * `$watchCollection`: Shallow watches the properties of an object and fires whenever any of the properties change (for arrays, this implies watching the array items; for object maps, this implies watching the properties). If a change is detected, the listener callback is fired.
* What are `$eval`, `$parse` and `$evalAsync`?
    * `$eval`: Executes the expression on the current scope and returns the result. Any exceptions in the expression are propagated (uncaught). This is useful when evaluating Angular expressions.
    * `$parse`: Converts Angular expression into a function.
    * `$evalAsync`: The $evalAsync makes no guarantees as to when the expression will be executed, only that:
        * it will execute after the function that scheduled the evaluation (preferably before DOM rendering).
        * at least one $digest cycle will be performed after expression execution.
* What is `$applyAsync`?
    * Schedule the invocation of $apply to occur at a later time. The actual time difference varies across browsers, but is typically around ~10 milliseconds.
    * This can be used to queue up multiple expressions which need to be evaluated in the same digest.
* What's a decorator in relation to angular's module system?
    * Decorators are a design pattern that is used to separate modification or decoration of a class without modifying the original source code. In Angular, decorators are functions that allow a service, directive or filter to be modified prior to its usage.
* How would you filter a large list with ng-repeat to include data from the server and client?
    * use pagination to reduce rendering time by limiting the size of the displayed list.
    ```
        module.controller('paginationController', function($scope) {
            $scope.currentPage = 0;
            $scope.pageSize = 75;
            $scope.setCurrentPage = function(currentPage) {
                $scope.currentPage = currentPage;
            };
            $scope.getNumberAsArray = function(num) {
                return new Array(num);
            };
            $scope.numPages = function() {
                return Math.ceil($scope.displayedList.length / $scope.pageSize);
            };
    ```
    ```
        angular.module('paginationApp').filter('start', function() {
            return function(input, start) {
                return input.slice(start);
            });
        });
    ```
    ```
        <tr ng-repeat="item in displayedList | start: currentPage * pageSize | limitTo:pageSize" /tr>
        <button ng-repeat="i in getNumberAsArray(numPages()) track by $index" ng-click="setCurrentPage($index)">{{$index + 1}}</button>
    ```
* How would you grab the `$injector`/`$scope` from the chrome console?
    * `$scope`: > angular.element(targetNode).scope()
        * > angular.element(targetNode).isolateScope()
        * use Batarang to inspect scope tree.
    * `$injector`: > angular.element(document.querySelector('html')).injector()
* Why is there ng-form?
    * the purpose of ngForm is to group controls, but not to be a replacement for the <form> tag with all of its capabilities (e.g. posting to the server, ...).
* How would you dynamically create forms?
    ```
        module.controller('controller', function($scope) {
            var users = [
                {
                    name: 'David',
                    email: ''
                },
                {
                    name: 'Jose',
                    email: ''
                }
            ];
            $scope.formData = {};
            $scope.formData.users = users;
        });
    ```
    ```
        <form name="userForm">
            <div ng-repeat="user in formData.users">
                <label>{{user.name}}'s email</label>
                <input type="text" name="email" ng-model="user.email">
            </div>
        </form>
    ```
* What's CSP and how does it relate to angular?
    * Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross-Site Scripting (XSS) and data injection attacks.
    * Angular has some features that can break certain CSP (Content Security Policy) rules.
        * `unsafe-eval`: this rule forbids apps to use `eval` or `Function(string)` generated functions (among other things). Angular makes use of this in the `$parse` service to provide a 30% increase in the speed of evaluating Angular expressions.
        * `unsafe-inline`: this rule forbids apps from injecting custom styles into the document. Angular makes use of this to include some CSS rules (e.g. `ngCloak` and `ngHide`). To make these directives work when a CSP rule is blocking inline styles, you must link to the angular-csp.css in your HTML manually.
* How do you structure your files for a large team/project?
    * Best practice is to structure the app such that you can locate your code quickly, identify the code at a glance, keep the flattest structure you can, and try to stay DRY. (LIFT)
    * Place components that define the overall layout of the application in a folder named `layout`.
    * Create folders named for the feature they represent.
    ```
        app/
            app.module.js
            app.config.js
            components/
                calendar.directive.js
                calendar.directive.html
                user-profile.directive.js
                user-profile.directive.html
            layout/
                shell.html
                shell.controller.js
                nav.html
                nav.controller.js
            services/
                data.service.js
                localstorage.service.js
                logger.service.js
                spinner.service.js
    ```
* How would you use a module loader/bundler such as browserify, webpack, or systemjs with angular?
    ```
        System.config({
            baseURL: "./",
            defaultJSExtensions: true,
            transpiler: "babel",
            babelOptions: {
                "optional": [
                    "runtime"
                ],
                "stage": 1
            },
            paths: {
                "employee-scheduling-ui/*": "src/*.js",
                "github:*": "jspm_packages/github/*",
                "npm:*": "jspm_packages/npm/*"
            },
            "map": {
                "angular": "github:angular/bower-angular@1.5.8",
                ...
            }
        });
    ```
    ```
        <script src="jspm_packages/system.js"></script>
        <script src="jspm.conf.js"></script>
        <script>
            System.import('app/bootstrap')
            .catch(console.error.bind(console));
        </script>
    ```
    ```
        import angular from 'angular';
        import mainModule from './main';
        angular.element(document).ready(function() {
            angular.bootstrap(document, [mainModule.name]);
        });
    ```
* How would you asynchronously load angular?
    * TODO
* How would you inject server rendered data into client angular?
    * TODO
* What's a document fragment?
    * The DocumentFragment interface represents a minimal document object that has no parent. It is used as a light-weight version of Document to store well-formed or potentially non-well-formed fragments of XML.
* What's the ShadowDOM?
    * Shadow DOM provides encapsulation for the JavaScript, CSS, and templating in a Web Component. Shadow DOM makes it so these things remain separate from the DOM of the main document. You can also use Shadow DOM by itself, outside of a web component.
* What is needed for your angular web app to work with JavaScript disabled?
    * hide all variables displayed through databindings using ng-cloak.
    ```
        <div ng-cloak>
            {{bound_data}}
        </div>
    ```
    ```
        [ng\:cloak], [ng-cloak], [data-ng-cloak], [x-ng-cloak], .ng-cloak, .x-ng-cloak {
            display: none !important;
        }
    ```
    * display alternate content when a user has JavaScript blocked or disabled.
    ```
        <noscript>
            You must have JavaScript enabled to use this app.
        </noscript>
    ```
* What is needed for your angular web app to be rendered on the server to be sent down to the client?
    * TODO
* Generally speaking how would you paraphrase angular?
    * AngularJS is a structural framework for dynamic web applications that lets the developer extend HTML.
* How would you progressively enhance your RESTful app with a pub/sub?
    * TODO
* How would you structure your app if you only had a realtime (pub/sub) API (no REST)?
    * TODO
* What are the different ways to architect your angular app?
    * structure the application by type. Controllers have their own directory, views have their own directory, etc.
    * structure the application by feature. controllers, views, factories related to a specific feature live in their own directory.
    * modularize header, footer, routes.
* What are the pros and cons of each design?
    * structure by type supports MVC, but does not scale well.
    * structure by feature supports modularization.
* What are some anti patterns developers tend to fall into while using angular?
    * don't wrap element inside of `$()`. All AngularJS elements are already jq-objects.
    * don't do `if (!$scope.$$phase) $scope.$apply()`, it means your `$scope.$apply()` isn't high enough in the call stack.
    * don't use jQuery to generate templates or DOM.
    * don't create a new plugin without trying to discover, fork and pull request existing plugins first.
    * don't use a scalar variable (null is scalar) as a model within an isolate scope (such as ng-if).
    * don't implement business logic inside of controllers.
    * don't rely on attaching objects to global scope.
* What are the problems currently facing angular1?
    * module loaders
    * performance issues
    * not platform-independent
* Explain how Angular 2 is solving all of the problems from 1.x
    * Angular 2 uses System.js as a module loader
    * Angular 2 uses components, removes scope.
    * change detection is improved.
    * Angular Universal, Mobile Toolkit allow for development on multiple platforms.
* Demonstrate a few ways to migrate an Angular 1 app to Angular 2
    * use the Upgrade Adapter to create hybrid Angular 1+2 applications
    ```
        import { UpgradeAdapter } from '@angular/upgrade';
        const upgradeAdapter = new UpgradeAdapter();
        upgradeAdapter.bootstrap(document.body, ['heroApp'], {strictDi: true});
    ```
    * use Angular 2 components from Angular 1 code
    ```
        import { HeroDetailComponent } from './hero-detail-component';
        angular.module('heroApp', [])
               .directive('heroDetail', upgradeAdapter.downgradeNg2Component(HeroDetailComponent));
    ```
    * use Angular 1 component directives from Angular 2 code
    ```
        import { Component } from '@angular/core';
        import { upgradeAdapter } from './upgrade_adapter';
        const HeroDetail = upgradeAdapter.upgradeNg1Component('heroDetail');
        @Component({
            selector: 'my-container',
            template: '<hero-detail></hero-detail>,
            directives: [HeroDetail]
        })
        export class ContainerComponent {}
    ```
    * projecting Angular 1 content into Angular 2 components
    ```
        @Component({
            selector: 'hero-detail',
            template: '<ng-content></ng-content>',
        })
        export class HeroDetailComponent {}
    ```
    ```
        <div ng-controller="MainController as mainCtrl">
            <hero-detail>
                <!-- everything here gets projected -->
            </hero-detail>
        </div>
    ```
    * transcluding Angular 2 content into Angular 1 component directives
    ```
        export const heroDetailComponent = {
            bindings: {
                hero: '='
            },
            template: '<ng-transclude></ng-transclude>
        };
    ```
    ```
        const HeroDetail = upgradeAdapter.upgradeNg1Component('heroDetail');
        @Component({
            selector: 'my-container',
            template: `
                <hero-detail [hero]="hero">
                    <!-- everything here will be transcluded -->
                </hero-detail>
            `,
            directives: [HeroDetail]
        })
        export class ContainerComponent { hero = new Hero(); }
    ```
    * making Angular 1 dependencies injectable to Angular 2
    ```
        angular.module('heroApp', [])
               .service('heroes', HeroesService);
        upgradeAdapter.upgradeNg1Provider('heroes');
    ```
    * making Angular 2 dependencies injectable to Angular 1
    ```
        angular.module('heroApp', [])
               .factory('heroes', upgradeAdapter.downgradeNg2Provider(Heroes));
    ```
* What's the difference between MVC, MVVM, MVP(SC), MVP(PV), PM, and how does it compare to Flux/Redux architecture?
    * Presentation Model: well-suited for rich UI applications. MVVM is a variation of PM.
    * MVP(Supervising Controller): view interacts with model directly to bind data to data controls without intervention of presenter. presenter is responsible for updating the model, manipulates the view only if necessary.
    * MVP(Passive View): view is not aware of model and presenter updates view to reflect changes in model.
    * main difference between MVP and MVC is that the Presenter refers back to the view, but the Controller does not.
    * MVVM can stand on its own while MVP cannot, MVP requires a View's interface)
    * use MVP in situations where binding via a datacontext is not possible: Windows Forms
    * use MVVM in situations where binding via a datacontext is possible, because the various interfaces for each view are removed which means less code to maintain.
    * use MVC in situations where the connection between the view and the rest of the program is not always available.
* How are dependencies handled when testing Angular controllers and services?
    * dependencies can be injected and stubbed or mocked as needed.
* How is `$scope` injected when testing Angular controllers?
    * inject $rootScope and create a child scope with `$scope = $rootScope.$new()`
* What is the purpose of wrapping core Angular providers and services in double underscores? ex: `_$rootScope_`?
    * underscores are a convenience trick that can be used to inject a service under a different name so that a local variable of the same name as the service can be locally assigned.
* Describe the necessary steps to test the Angular `$http` service
    * inject the `$httpBackend`
    * use `$httpBackend.expect` to specify a request expectation.
    * use `$httpBackend.when` to specify a backend definition.
    * verify no outstanding expectations or requests.
* How would you test an `$http` request to a third party API such as Youtube?
    ```
        $httpBackend.when('/data').respond({data: 'data'});
    ```
* How would you test the data being returned from the API request?
    ```
        expect(data).toBe('data');
    ```
* What frameworks, languages and tools are available for testing in Angular?
    * Karma, Jasmine, Protractor
* How is $scope used when testing Angular controllers?
    * $scope must be created as a new child from `$rootScope.$new()`
* Explain what `$httpBackend` and `$httpBackend.flush` are used for
    * `$httpBackend`: Fake HTTP backend implementation suitable for unit testing applications that use the $http service.
    * `$httpBackend.flush`: allows the test to explicitly flush pending requests. This preserves the async api of the backend, while allowing the test to execute synchronously.
* Explain what `angular.mock` is used for
    * the namespace from angular-mocks.js that contains testing related code.
