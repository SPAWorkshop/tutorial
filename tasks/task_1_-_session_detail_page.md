# Task 1 - Session detail page

## Goal

We want to have a separate web page on which user can see detail of the session: it's name, start time and list of talks.

In addition, we want to show loader indicator when UI waits for the API response.

## Objectives

### Frontend

- Each item at session list page template has proper link to the detail page. It should point the browser to something like `/#/session/102`.
- Add an entry at route configuration connecting session detail link with a controller and template. *Hint: route configuration can be found at `app.js` file.*
- At `SessionDetailCtrl` fetch `Session` object from the API and store it at the controller's scope. *Hint: we can use `$routeParams` to access current's route parameters, like session's ID number.*
- Extend session detail template - use real data instead of the placeholders. In addition, hide talk list and show a warning message when there are no talks for this session yet. Moreover, we want to show loader indicator when user waits for the server response.


### Backend

- Add an entry at route configuration (`urls.py`) for session detail endpoint.
- Add session detail *view* - code responsible for returning a response for that endpoint.
- Create needed serializers which would build JSON data for the `Session` fetched from the database. *Hint: we would need a talk list for the session and for each talk we also want it's author first/last names.*
