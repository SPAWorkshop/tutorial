# Task 4 - Update talk

## Goal

User should be able to update the title of a submitted talk.

## Objectives

### Frontend

- Add handler for `PUT` method at the `Talk` service
- At the talk update template:
    - bind inputs with controller properties
    - add form submit handler
    - add general loader
    - add button loader
    - display errors
- At the talk update controller:
    - fetch talk
    - handle errors (forbidden)
    - create form submit handler
    - send talk data to backend
    - handle success
    - show toast message
    - redirect to talks list
    - handle errors
    - force user to be logged in

### Backend

- Create custom permission: only author of a talk should be able to update her objects.

