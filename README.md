# SQL Exercises — SQLBolt Solutions

A structured collection of SQL exercise solutions based on the interactive lessons from [SQLBolt](https://sqlbolt.com/). Each lesson covers a core SQL concept, with the original question, reference table, queries, and expected output all documented in one place.

---

## Table of Contents

| # | Lesson | Topic |
|---|--------|-------|
| 01 | [SELECT queries 101](Question1.md) | Selecting columns from a table |
| 02 | [Queries with constraints (Pt. 1)](Question2.md) | Filtering rows with WHERE and numerical operators |

---

## Repository Structure

```
sql-exercises/
├── README.md
└── lessons/
    ├── lesson-01-select-queries.md
    ├── lesson-02-constraints-pt1.md
    └── ...
```

---

## How Each Lesson File Is Organized

Every lesson markdown file follows the same consistent format:

1. **Concept overview** — a brief explanation of the SQL topic covered
2. **Reference table** — the dataset used in the exercise
3. **Tasks & Solutions** — each task listed with its query and output

---

## Database Used

Most exercises use a **Pixar movies** database. The main tables include:

- `movies` — title, director, year, length_minutes
- `boxoffice` — movie_id, rating, domestic_sales, international_sales

Some later lessons introduce additional tables for JOIN exercises.

---

## Source

All exercises are sourced from [SQLBolt](https://sqlbolt.com/) — a free, interactive SQL learning site. This repository exists purely for learning and reference purposes.
