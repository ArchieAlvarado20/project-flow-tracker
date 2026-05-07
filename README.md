# 🧩 Dev Task Tracker

A simple and lightweight developer task tracker built with **vanilla HTML, CSS, and JavaScript**.  
Designed for managing feature development, requirements, issues, and progress tracking in a clean dashboard UI.

---

## 🚀 Features

- 📝 Create and manage tasks
- 📌 Track status (Pending, In Progress, Testing, Done, Blocked)
- ✅ Requirement checklist per task
- 🐞 Issue tracking per feature
- 📋 Notes section for documentation
- ✔️ Tested & Completed indicators
- 🔴 / 🟢 Ready status detection
- ✏️ Edit existing tasks using same form
- 🗑️ Delete tasks with confirmation
- 💾 Auto-save using `localStorage`
- 📤 Export / 📥 Import JSON backup
- 📋 Paste JSON import support
- 📱 Responsive grid layout (desktop, tablet, mobile)

---

## 🛠️ Tech Stack

- HTML5
- CSS3 (custom styling, responsive grid)
- JavaScript (Vanilla JS)
- Browser `localStorage`

---

## 📂 Data Storage

This project uses browser `localStorage`:

- No backend required
- Data stays in the current browser/device
- Supports manual backup via Export/Import JSON

---

## 📦 Backup System

### Export Data
Download all tasks as a JSON file.

### Import Data
Restore tasks via:
- File upload (.json)
- Paste JSON directly

---

## 💡 Use Case

This tool is ideal for:

- Personal developer task tracking
- Small project management
- Feature progress monitoring
- Learning CRUD concepts in JavaScript
- Offline-first productivity apps

---

## 📸 UI Preview


## 📸 Screenshot & Report Instructions

To report UI updates or issues:

1. Press **Win + Shift + S** to open Snipping Tool.
2. Select **Rectangular Snip** and drag to capture the card or UI section.
3. The screenshot will be copied automatically to your clipboard.
4. Paste it using **Ctrl + V** in your message or report.
5. Add a short description and send it to your boss or reviewer.

# Task JSON Structure — Pattern Reference

This document defines the JSON schema used for each task in this project.
All AI-generated or manually created tasks must follow this pattern exactly.

---

## Single Task Object

```json
{
  "id": 1,
  "title": "1. Task title here",
  "description": "One to two sentence explanation of what this task does and why it exists.",
  "status": "in-progress",
  "requirements": [
    { "text": "Specific requirement or sub-task", "done": false },
    { "text": "Another requirement", "done": false }
  ],
  "issues": [
    "Known blocker or problem (string, plain text)"
  ],
  "notes": "Additional context, technical decisions, or reminders for this task.",
  "tested": false,
  "completed": false
}
```

---

## Field Reference

| Field          | Type             | Required | Description                                                                 |
|----------------|------------------|----------|-----------------------------------------------------------------------------|
| `id`           | `number`         | Yes      | Unique task number. Must match the number prefix in `title`. Sequential.   |
| `title`        | `string`         | Yes      | Format: `"<id>. <Task name>"` — e.g. `"3. Browse events and activities"`  |
| `description`  | `string`         | Yes      | Brief explanation of the task's purpose and scope.                         |
| `status`       | `string (enum)`  | Yes      | Current state. Allowed values: `"in-progress"`, `"ready"`, `"blocked"`    |
| `requirements` | `array`          | Yes      | List of sub-tasks. Each item has `text` (string) and `done` (boolean).     |
| `issues`       | `array<string>`  | Yes      | Known blockers or concerns. Empty array `[]` if none.                      |
| `notes`        | `string`         | Yes      | Free-text notes, decisions, or reminders. Empty string `""` if none.      |
| `tested`       | `boolean`        | Yes      | Set to `true` only when the task has been manually tested end-to-end.      |
| `completed`    | `boolean`        | Yes      | Set to `true` only when all requirements are done and task is verified.    |

---

## Status Values

| Value         | Meaning                                              |
|---------------|------------------------------------------------------|
| `in-progress` | Task is being worked on or not yet started           |
| `ready`       | Task is done and ready for demo or review            |
| `blocked`     | Task cannot proceed due to a dependency or issue     |

---

## Requirements Item Pattern

```json
{ "text": "Description of the sub-task", "done": false }
```

- `text` — what needs to be done (string)
- `done` — whether this specific requirement is finished (boolean)

---

## Full Array Pattern

All tasks are stored as an array of objects:

```json
[
  { "id": 1, "title": "1. ...", ... },
  { "id": 2, "title": "2. ...", ... },
  { "id": 3, "title": "3. ...", ... }
]
```

- `id` values must be sequential and unique
- `id` must always match the number prefix in `title`
- Do not skip or duplicate IDs

---

## Rules for AI Prompting

When asking an AI to generate tasks using this pattern:

1. Always provide this README as context before the request
2. Specify the starting `id` number if appending to existing tasks
3. Every generated object must include **all fields** — no field may be omitted
4. `issues` and `notes` must never be omitted — use `[]` and `""` if empty
5. `tested` and `completed` must always default to `false` unless explicitly stated
6. `status` must be one of the three allowed values only

---

## Example Prompt

```
Using the task JSON pattern in the README, generate tasks for the following features.
Start from id 27. Return a valid JSON array only, no explanation.

Features:
- Admin dashboard
- Export reports to CSV
```





Use this when sharing UI updates, bugs, or design feedback.
