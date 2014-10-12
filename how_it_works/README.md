# How it works

## Frontend

After running `gulp` command browser should be opened and you should see a session
list, similar to the one from Figure 1.

![Figure 1](../images/session-list.png)

### Url handler

Let's have a look at (simplified) Angular application definition.

```javascript
angular.module('lightningtalks', ['ngRoute'])
  .config(function ($routeProvider, $httpProvider) {

    $routeProvider
      .when('/', {
        templateUrl: 'partials/sessions/session-list.html',
        controller: 'SessionListCtrl'
      });
```

What's important here is `$routeProvider.when` method. We can seee that `/` url
is bound to the `session-list.html` template and is handled by `SessionListCtrl`.

We will describe briefly what's going on on a template.

### The View

Here is our `session-list.html` template's content (again, simplified):

```html
<div class="sessions">
  <ul class="sessions__list">
    <li class="sessions__item" ng-repeat="session in sessions">
      <h2>{{ session.name }}</h2>
    </li>
  </ul>
</div>
```

Note that cryptic `ng-repeat="session in sessions"` attribute declaration at the `li` element.
It means that `li` element should be repeated for each item within `sessions` object. We might
assume that this object is an array of session objects.

> Tip: Angular provides some helpers to get the *scope* of an HTML element. You can open
> developer tools in your browser and type into console:
> `angular.element('.sessions__list').scope()` to see a Javascript object that is bound
> to the element.

But how was that `sessions` set on the scope?

### The Controller

Firstly let us have a look at the controller's code:

```js
angular.module('lightningtalks')
  .controller('SessionListCtrl', function ($scope, Session) {
    $scope.sessions = Session.query();
  });
```

Actually, there is not much going on here. In fact, our controller is responsible only
for setting `sessions` object at the `$scope`. So our `sessions` is the result of the `Session.query()` method call. And the `Session` object is an custom *service* which defines the model.

### The Model

In our example model is a result of the API endpoint call. AngularJS provides low level `$http` object for communication over HTTP, however it also gives us a nice API resources wrapper. At `session-service.js` file we can see something similar to:

```js
angular.module('lightningtalks')
  .service('Session', function ($resource) {
    return $resource('http://localhost:8000/api/sessions/:id');
  });

```

With that service definition we can use `Session` object and it's methods to talk with our API server.
