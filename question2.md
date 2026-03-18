# Lesson 02 — Queries with Constraints (Pt. 1)

> **Source:** [SQLBolt — Lesson 2](https://sqlbolt.com/lesson/select_queries_with_constraints)

---

## Concept

To filter results from a query, we use a `WHERE` clause. It is applied to each row by checking specific column values to determine whether that row should be included in the results.

### Syntax

```sql
SELECT column, another_column, …
FROM mytable
WHERE condition
    AND/OR another_condition
    AND/OR …;
```

### Numerical Operators

| Operator | Condition | SQL Example |
|----------|-----------|-------------|
| `=`, `!=`, `<`, `<=`, `>`, `>=` | Standard numerical operators | `col_name != 4` |
| `BETWEEN … AND …` | Number is within range (inclusive) | `col_name BETWEEN 1.5 AND 10.5` |
| `NOT BETWEEN … AND …` | Number is not within range (inclusive) | `col_name NOT BETWEEN 1 AND 10` |
| `IN (…)` | Number exists in a list | `col_name IN (2, 4, 6)` |
| `NOT IN (…)` | Number does not exist in a list | `col_name NOT IN (1, 3, 5)` |

> **Note:** SQL keywords don't need to be capitalized, but it's a widely used convention to distinguish them from column and table names.

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

---

## Tasks & Solutions

---

### Task 1 — Find the movie with a row `id` of 6

```sql
SELECT * FROM movies
WHERE id = 6;
```

**Output:**

| id | title | directory | year | length_minutes |
|----|-------|-----------|------|----------------|
| 6 | The Incredibles | Brad Bird | 2004 | 116 |

---

### Task 2 — Find the movies released in the `year`s between 2000 and 2010

```sql
SELECT * FROM movies
WHERE year BETWEEN 2000 AND 2010;
```

**Output:**

| id | title | directory | year | length_minutes |
|----|-------|-----------|------|----------------|
| 4 | Monsters, Inc. | Pete Docter | 2001 | 92 |
| 5 | Finding Nemo | Andrew Stanton | 2003 | 107 |
| 6 | The Incredibles | Brad Bird | 2004 | 116 |
| 7 | Cars | John Lasseter | 2006 | 117 |
| 8 | Ratatouille | Brad Bird | 2007 | 115 |
| 9 | WALL-E | Andrew Stanton | 2008 | 104 |
| 10 | Up | Pete Docter | 2009 | 101 |
| 11 | Toy Story 3 | Lee Unkrich | 2010 | 103 |

---

### Task 3 — Find the movies not released in the `year`s between 2000 and 2010

```sql
SELECT * FROM movies
WHERE year NOT BETWEEN 2000 AND 2010;
```

**Output:**

| id | title | directory | year | length_minutes |
|----|-------|-----------|------|----------------|
| 1 | Toy Story | John Lasseter | 1995 | 81 |
| 2 | A Bug's Life | John Lasseter | 1998 | 95 |
| 3 | Toy Story 2 | John Lasseter | 1999 | 93 |
| 12 | Cars 2 | John Lasseter | 2011 | 120 |
| 13 | Brave | Brenda Chapman | 2012 | 102 |
| 14 | Monsters University | Dan Scanlon | 2013 | 110 |

---

### Task 4 — Find the first 5 Pixar movies and their release `year`

```sql
SELECT title, year FROM movies
WHERE id IN (1, 2, 3, 4, 5);
```

**Output:**

| title | year |
|-------|------|
| Toy Story | 1995 |
| A Bug's Life | 1998 |
| Toy Story 2 | 1999 |
| Monsters, Inc. | 2001 |
| Finding Nemo | 2003 |

---

## Key Takeaways

- `WHERE` filters rows based on a condition before returning results
- `BETWEEN … AND …` is inclusive on both ends
- `NOT BETWEEN` and `NOT IN` are useful for excluding specific ranges or values
- Multiple conditions can be combined with `AND` / `OR`
- Filtering early makes queries faster by reducing unnecessary data retrieval
