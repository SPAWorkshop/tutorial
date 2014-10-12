# Task 3 - Limit the number of talks per session

## Goal

Aim of this task is to limit the number of talks that user can add to single session.

## Objectives

### Frontend

- At the creation talk template we need to display the number of talks
- if session has already maximum number of talks:
  * disable "Add talk" button
  * mark talks number counter with red color

### Backend

- Add new field to `Session` model (`max_talks`)
- Remember to add a migration after changing the model.
- Run migration in order to actually change state of the database.
- Implement validation at the talk serializer when creating new talk.
