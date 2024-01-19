# Relog Export Format, Version 2

## A Few Notes

- All dates are represented as the time in seconds since 00:00:00 UTC on 1 January 2001.
- Categories must have unique names. No duplicate categories will be imported.
- For simplicity, the import process in Relog is [atomic](https://en.wikipedia.org/wiki/Atomicity\_\(database\_systems). If any keys are missing or any data is malformed, the import process will fail.
- All keys are required.
- User data can currently only be imported and exported using `JSON`.


## Top Level

| Key           | Type       | Description                                                              |
| ------------- | ---------- | ------------------------------------------------------------------------ |
| date_exported | Date       | When this export was created                                             |
| model_version | Int        | the version of the export format. All public versions of Relog use **2** |
| tasks         | [Task]     | a list of tasks                                                          |
| Categories    | [Category] | a list of categories                                                     |

## Category

| key           | Type   | Description                                                     |
| ------------- | ------ | --------------------------------------------------------------- |
| category_name | String | the name of the category (min: 1 character, max: 32 characters) |


## Task
| Key                  | Type         | Description                                                                                               |
| -------------------- | ------------ | --------------------------------------------------------------------------------------------------------- |
| name                 | String       | the name of the task (min: 1 character, max: 32 characters)                                               |
| accent_color_id      | Int          | a representation of the tasks accent color                                                                |
| category             | String       | the name of the category                                                                                  |
| icon_identifier      | String       | an SF symbol icon name                                                                                    |
| task_description     | String       | the tasks description (min 0 characters, max 512 characters)                                              |
| show_in_upcoming_tab | Boolean      | Whether the task will show in the upcoming tab if it hasn't been completed after a certain period of time |
| upcoming_period      | Int          | how many of the unit (i.e. 1 day, 3 weeks, etc)                                                           |
| upcoming_unit_id     | Int          | A representation of the unit (day, week, month, year)                                                     |
| completions          | [Completion] | A list of the tasks completions    

### Possible Accent Colors

| Color | Id     |
| ----- | ------ |
| 0     | Red    |
| 1     | Orange |
| 2     | Yellow |
| 3     | Green  |
| 4     | Mint   |
| 5     | Teal   |
| 6     | Cyan   |
| 7     | Blue   |
| 8     | Indigo |
| 9     | Purple |
| 10    | Pink   |
| 11    | Brown  |

### Upcoming Units

| Unit  | Id |
| ----- | -- |
| Hour  | 0  |
| Day   | 1  |
| Week  | 2  |
| Month | 3  |
| Year  | 4  |


## Completion

| Key            | Type   | Description                                                                  |
| -------------- | ------ | ---------------------------------------------------------------------------- |
| date_completed | Date   | when this completion occured                                                 |
| note           | String | a note associated with the completion (min 0 characters, max 512 characters) |

