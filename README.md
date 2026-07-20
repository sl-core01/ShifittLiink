# ShiftLink Python Version

ShiftLink is a cram school shift management app.

The screen is made with `index.html` using HTML / CSS / JavaScript.
The backend is added with Python Flask in `backend.py`.

## Files

- `index.html`
  - Frontend screen
  - Calls Python API from JavaScript

- `backend.py`
  - Python Flask backend
  - Handles login, teacher registration, shift saving, shift summary, demo lesson saving, and demo lesson summary

- `requirements.txt`
  - Python libraries

- `shiftlink_data.json`
  - JSON data file created automatically when the backend runs

## Python Topics Used

| Topic | How it is used |
|---|---|
| variable | `DATA_FILE`, `app`, `store`, `service` |
| list | `teachers`, `shiftRequests`, `demoLessons`, `required_fields`, `missing_fields`, `input_items` |
| dict | teacher data, shift data, demo lesson data, summary data |
| tuple | demo lesson sort key and teacher input pairs such as `("name", "")` |
| set | unique assigned teacher IDs |
| if / elif / else | login check, required input check, demo lesson status check |
| for | `range(0, 10)`, `enumerate()`, `.items()`, and list loops |
| function | `default_data()`, `normalize_text()`, `generate_password()`, `prepare_teacher_input()` |
| JSON I/O | load and save `shiftlink_data.json` |
| class / OOP | `JsonStore`, `ShiftLinkService` |
| random | random password generation for teacher registration |

## Class Topic Map

This project intentionally uses class topics in real app features.

- INPUT
  - HTML input values are sent from JavaScript to Flask.
  - Python receives them with `get_input_payload()`.

- PRINT
  - `log_event()` uses `print()` to show backend actions in the terminal.
  - Examples: login success, teacher saved, shift saved, demo lesson saved.

- IF
  - Login success/failure.
  - Required input validation.
  - Demo lesson status checks.

- FOR
  - Required fields are checked one by one.
  - Random password numbers are generated with `range(0, 10)`.
  - Teacher rows are counted with `enumerate()`.
  - Dictionary data is saved with `.items()`.
  - Demo lessons are counted one by one.

- LIST
  - `missing_fields`, `required_fields`, `password_parts`, `share_text_lines`.

- FUNCTION
  - Repeated logic is separated into functions such as `generate_password()` and `count_by_key()`.

- SET
  - Unique teacher IDs, roles, and subjects are collected with `set`.

- TUPLE
  - Demo lessons are sorted by tuple key.
  - Teacher input fields are stored as `(key, default_value)` pairs.

## Teacher Registration Logic

Teacher registration uses data typed into HTML input fields.
JavaScript sends that input data to Python API.

Python then does these steps:

1. Receive input data as a dictionary.
2. Clean text values with `normalize_text()`.
3. Clean full-width spaces using `replace()`.
4. Check required fields using a list named `required_fields`.
5. Use a for loop to find missing fields.
6. If password is empty, create a random password with `generate_password()`.
7. Save the teacher data to `shiftlink_data.json`.

Main functions:

- `prepare_teacher_input(input_data)`
  - Prepares teacher input data with a list of tuple pairs.

- `validate_required_fields(data, required_fields)`
  - Uses list, for loop, and if statement to check required fields.

- `generate_password()`
  - Uses `for i in range(0, 10)`, `random.randint(0, 9)`, and a list.

- `teacher_summary()`
  - Uses list, set, tuple, `enumerate()`, for, and dict to summarize teacher accounts.

## Demo Lesson Logic

Demo lesson features also use many Python basics.

- `demo_lessons_sorted()`
  - Sorts demo lessons by date, visit time, and demo time.
  - Uses a tuple as the sort key.

- `demo_lessons_by_status(status)`
  - Uses a list, for loop, and if statement to filter demo lessons.

- `demo_lessons_for_teacher(teacher_id)`
  - Filters demo lessons by assigned teacher.

- `demo_summary()`
  - Uses dict to count demo lesson status.
  - Uses `+=` to add counts.
  - Uses set to count unique assigned teachers.
  - Uses list to create share text lines.
  - Uses `.format()` to create share text.
  - Uses `count_by_key()` to count subjects.
  - Creates share text lines without student names.

## How To Run

Move to this folder in Command Prompt.

```cmd
cd C:\Users\dream\Documents\Codex\2026-07-10\files-mentioned-by-the-user-index\outputs\github-python-version
```

Install libraries.

```cmd
python -m pip install -r requirements.txt
```

Run Python backend.

```cmd
python backend.py
```

Success message:

```text
Running on http://127.0.0.1:5000
```

Health check URL:

```text
http://127.0.0.1:5000/api/health
```

## GitHub Pages

GitHub Pages can publish `index.html`.

GitHub Pages cannot run Python.
So `backend.py` is included as the Python backend source code, and it should be run on a PC for testing.
