# Task 2 - Create talk

## Goal

We want to allow authorized user to be able to submit talk to one of the existing session.

## Objectives

### Frontend

- At the `TalkCreateCtrl` we need to:
  * create action that would handle form submission
  * send provided data to proper API endpoint
  * on success:
    - show success toast message
    - redirect to the "My talks" list
  * on error:
    - show validation messages at the form

### Backend

- Make sure `Talk.author` is set to currently signed in user before talk is saved
