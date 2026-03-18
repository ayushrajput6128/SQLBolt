# Lesson 01 — SELECT Queries 101

> **Source:** [SQLBolt — Lesson 1](https://sqlbolt.com/lesson/select_queries_introduction)

---

## Concept

To retrieve data from a SQL database, we write `SELECT` statements (commonly called **queries**). A query declares:
- **What** data we are looking for
- **Where** to find it in the database
- Optionally, **how** to transform it before it's returned

You can think of a table as a type of entity (e.g. *Dogs*), each row as a specific instance (e.g. a pug, a beagle), and each column as a shared property (e.g. fur color, tail length).

### Syntax

Select specific columns:
```sql
SELECT column, another_column FROM mytable;
```

Select all columns:
```sql
SELECT * FROM mytable;
```

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

### Task 1 — Find the `title` of each film

```sql
SELECT title FROM movies;
```

**Output:**

| title |
|-------|
| Toy Story |
| A Bug's Life |
| Toy Story 2 |
| Monsters, Inc. |
| Finding Nemo |
| The Incredibles |
| Cars |
| Ratatouille |
| WALL-E |
| Up |
| Toy Story 3 |
| Cars 2 |
| Brave |
| Monsters University |

---

### Task 2 — Find the `directory` of each film

```sql
SELECT directory FROM movies;
```

**Output:**

| directory |
|-----------|
| John Lasseter |
| John Lasseter |
| John Lasseter |
| Pete Docter |
| Andrew Stanton |
| Brad Bird |
| John Lasseter |
| Brad Bird |
| Andrew Stanton |
| Pete Docter |
| Lee Unkrich |
| John Lasseter |
| Brenda Chapman |
| Dan Scanlon |

---

### Task 3 — Find the `title` and `directory` of each film

```sql
SELECT title, directory FROM movies;
```

**Output:**

| title | directory |
|-------|-----------|
| Toy Story | John Lasseter |
| A Bug's Life | John Lasseter |
| Toy Story 2 | John Lasseter |
| Monsters, Inc. | Pete Docter |
| Finding Nemo | Andrew Stanton |
| The Incredibles | Brad Bird |
| Cars | John Lasseter |
| Ratatouille | Brad Bird |
| WALL-E | Andrew Stanton |
| Up | Pete Docter |
| Toy Story 3 | Lee Unkrich |
| Cars 2 | John Lasseter |
| Brave | Brenda Chapman |
| Monsters University | Dan Scanlon |

---

### Task 4 — Find the `title` and `year` of each film

```sql
SELECT title, year FROM movies;
```

**Output:**

| title | year |
|-------|------|
| Toy Story | 1995 |
| A Bug's Life | 1998 |
| Toy Story 2 | 1999 |
| Monsters, Inc. | 2001 |
| Finding Nemo | 2003 |
| The Incredibles | 2004 |
| Cars | 2006 |
| Ratatouille | 2007 |
| WALL-E | 2008 |
| Up | 2009 |
| Toy Story 3 | 2010 |
| Cars 2 | 2011 |
| Brave | 2012 |
| Monsters University | 2013 |

---

### Task 5 — Find all the information about each film

```sql
SELECT * FROM movies;
```

**Output:**

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

## Key Takeaways

- `SELECT column1, column2 FROM table` returns only the specified columns
- `SELECT *` returns every column — useful for quickly inspecting a table
- Column order in `SELECT` determines the order in the output
