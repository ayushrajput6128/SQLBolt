# Lesson 03 — Queries with Constraints (Pt. 2)

> **Source:** [SQLBolt — Lesson 3](https://sqlbolt.com/lesson/select_queries_with_constraints_pt_2)

---

## Concept

When filtering columns that contain **text data**, SQL supports string-specific operators for exact matches, pattern matching, and list checks.

### Syntax

```sql
SELECT column, another_column, …
FROM mytable
WHERE condition
    AND/OR another_condition
    AND/OR …;
```

### String Operators

| Operator | Condition | Example |
|----------|-----------|---------|
| `=` | Case-sensitive exact match | `col_name = "abc"` |
| `!=` or `<>` | Case-sensitive exact inequality | `col_name != "abcd"` |
| `LIKE` | Case-insensitive exact match | `col_name LIKE "ABC"` |
| `NOT LIKE` | Case-insensitive exact inequality | `col_name NOT LIKE "ABCD"` |
| `%` | Matches zero or more characters (with `LIKE`/`NOT LIKE`) | `col_name LIKE "%AT%"` |
| `_` | Matches exactly one character (with `LIKE`/`NOT LIKE`) | `col_name LIKE "AN_"` |
| `IN (…)` | String exists in a list | `col_name IN ("A", "B", "C")` |
| `NOT IN (…)` | String does not exist in a list | `col_name NOT IN ("D", "E", "F")` |

> **Note:** All strings must be quoted so the query parser can distinguish them from SQL keywords. For heavy full-text search needs, dedicated libraries like Apache Lucene or Sphinx are more efficient than SQL operators.

---

## Reference Table: `movies`

| id | title | directory | year | length_minutes |
|----|-------|-----------|------|----------------|
| 1 | Toy Story | John Lasseter | 1995 | 81 |
| 2 | A Bug's Life | John Lasseter | 1998 | 95 |
| 3 | Toy Story 2 | John Lasseter | 1999 | 93 |
| 4 | Monsters, Inc. | Pete Docter | 2001 | 92 |
| 5 | Finding Nemo | Andrew Stanton | 2003 | 107 |
| 6 | The Incredibles | Brad Bird | 2004 | 116 |
| 7 | Cars | John Lasseter | 2006 | 117 |
| 8 | Ratatouille | Brad Bird | 2007 | 115 |
| 9 | WALL-E | Andrew Stanton | 2008 | 104 |
| 10 | Up | Pete Docter | 2009 | 101 |
| 11 | Toy Story 3 | Lee Unkrich | 2010 | 103 |
| 12 | Cars 2 | John Lasseter | 2011 | 120 |
| 13 | Brave | Brenda Chapman | 2012 | 102 |
| 14 | Monsters University | Dan Scanlon | 2013 | 110 |
| 87 | WALL-G | Brenda Chapman | 2042 | 97 |

---

## Tasks & Solutions

---

### Task 1 — Find all the Toy Story movies

```sql
SELECT * FROM movies
WHERE title LIKE "Toy Story%";
```

**Output:**

| id | title | directory | year | length_minutes |
|----|-------|-----------|------|----------------|
| 1 | Toy Story | John Lasseter | 1995 | 81 |
| 3 | Toy Story 2 | John Lasseter | 1999 | 93 |
| 11 | Toy Story 3 | Lee Unkrich | 2010 | 103 |

---

### Task 2 — Find all the movies directed by John Lasseter

```sql
SELECT * FROM movies
WHERE directory LIKE "John Lasseter";
```

**Output:**

| id | title | directory | year | length_minutes |
|----|-------|-----------|------|----------------|
| 1 | Toy Story | John Lasseter | 1995 | 81 |
| 2 | A Bug's Life | John Lasseter | 1998 | 95 |
| 3 | Toy Story 2 | John Lasseter | 1999 | 93 |
| 7 | Cars | John Lasseter | 2006 | 117 |
| 12 | Cars 2 | John Lasseter | 2011 | 120 |

---

### Task 3 — Find all the movies (and director) not directed by John Lasseter

```sql
SELECT title, directory FROM movies
WHERE directory NOT LIKE "John Lasseter";
```

**Output:**

| title | directory |
|-------|-----------|
| Monsters, Inc. | Pete Docter |
| Finding Nemo | Andrew Stanton |
| The Incredibles | Brad Bird |
| Ratatouille | Brad Bird |
| WALL-E | Andrew Stanton |
| Up | Pete Docter |
| Toy Story 3 | Lee Unkrich |
| Brave | Brenda Chapman |
| Monsters University | Dan Scanlon |
| WALL-G | Brenda Chapman |

---

### Task 4 — Find all the WALL-* movies

```sql
SELECT * FROM movies
WHERE title LIKE "WALL-%";
```

**Output:**

| id | title | directory | year | length_minutes |
|----|-------|-----------|------|----------------|
| 9 | WALL-E | Andrew Stanton | 2008 | 104 |
| 87 | WALL-G | Brenda Chapman | 2042 | 97 |

---

## 💡 Key Takeaways

- `LIKE` is case-insensitive; `=` is case-sensitive
- `%` is a wildcard for zero or more characters — useful for prefix/suffix/substring matching
- `_` matches exactly one character
- `NOT LIKE` and `NOT IN` exclude matching rows
- Always quote strings in SQL to avoid conflicts with keywords
