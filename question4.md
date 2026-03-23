# Lesson 04 — Filtering and Sorting Query Results

> **Source:** [SQLBolt — Lesson 4](https://sqlbolt.com/lesson/filtering_sorting_query_results)

---

## Concept

### Removing Duplicates with DISTINCT

Query results can contain duplicate values across rows. Use `DISTINCT` to discard rows with duplicate column values.

```sql
SELECT DISTINCT column, another_column, …
FROM mytable
WHERE condition(s);
```

### Ordering Results with ORDER BY

Data in a database is rarely stored in a useful order. Use `ORDER BY` to sort results alphanumerically by a column, ascending or descending.

```sql
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC;
```

### Limiting Results with LIMIT and OFFSET

Use `LIMIT` to cap the number of rows returned, and `OFFSET` to skip a number of rows before starting to count.

```sql
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

> **Note:** `LIMIT` and `OFFSET` are applied last, after all other clauses. This is covered in detail in Lesson 12.

---

## Reference Table: `movies`

>  This lesson uses a **scrambled** version of the movies table to mimic real-world data. Note that the column is named `director` here.

| id | title | director | year | length_minutes |
|----|-------|----------|------|----------------|
| 1 | A Bug's Life | John Lasseter | 1998 | 95 |
| 2 | Ratatouille | Brad Bird | 2007 | 115 |
| 3 | Brave | Brenda Chapman | 2012 | 102 |
| 4 | Cars | John Lasseter | 2006 | 117 |
| 5 | Monsters, Inc. | Pete Docter | 2001 | 92 |
| 6 | Toy Story 2 | John Lasseter | 1999 | 93 |
| 7 | Finding Nemo | Andrew Stanton | 2003 | 107 |
| 8 | Toy Story | John Lasseter | 1995 | 81 |
| 9 | WALL-E | Andrew Stanton | 2008 | 104 |
| 10 | Up | Pete Docter | 2009 | 101 |
| 11 | The Incredibles | Brad Bird | 2004 | 116 |
| 12 | Cars 2 | John Lasseter | 2011 | 120 |
| 13 | Toy Story 3 | Lee Unkrich | 2010 | 103 |
| 14 | Monsters University | Dan Scanlon | 2013 | 110 |

---

## Tasks & Solutions

---

### Task 1 — List all directors of Pixar movies (alphabetically), without duplicates

```sql
SELECT DISTINCT director FROM movies
ORDER BY director ASC;
```

**Output:**

| director |
|----------|
| Andrew Stanton |
| Brad Bird |
| Brenda Chapman |
| Dan Scanlon |
| John Lasseter |
| Lee Unkrich |
| Pete Docter |

---

### Task 2 — List the last four Pixar movies released (ordered from most recent to least)

```sql
SELECT title, year FROM movies
ORDER BY year DESC
LIMIT 4;
```

**Output:**

| title | year |
|-------|------|
| Monsters University | 2013 |
| Brave | 2012 |
| Cars 2 | 2011 |
| Toy Story 3 | 2010 |

---

### Task 3 — List the first five Pixar movies sorted alphabetically

```sql
SELECT title FROM movies
ORDER BY title ASC
LIMIT 5;
```

**Output:**

| title |
|-------|
| A Bug's Life |
| Brave |
| Cars |
| Cars 2 |
| Finding Nemo |

---

### Task 4 — List the next five Pixar movies sorted alphabetically

```sql
SELECT title FROM movies
ORDER BY title ASC
LIMIT 5 OFFSET 5;
```

**Output:**

| title |
|-------|
| Monsters University |
| Monsters, Inc. |
| Ratatouille |
| The Incredibles |
| Toy Story |

---

## Key Takeaways

- `DISTINCT` removes duplicate values from results — useful when selecting a single column like a list of directors
- `ORDER BY column ASC` sorts A→Z or lowest→highest; `DESC` reverses it
- `LIMIT n` returns at most `n` rows; `OFFSET n` skips the first `n` rows before counting
- Combining `ORDER BY` + `LIMIT` + `OFFSET` is the standard pattern for pagination
