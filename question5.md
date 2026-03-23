# Review 01 — Simple SELECT Queries

> **Source:** [SQLBolt — Review 1](https://sqlbolt.com/lesson/select_queries_review)

---

## Concept

This is a review of all the SELECT query clauses covered so far, applied to a new table.

```sql
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

---

## Reference Table: `north_american_cities`

> **Note:** Positive latitudes = northern hemisphere. Positive longitudes = eastern hemisphere. All North American cities have positive latitudes and negative longitudes.

| city | country | population | latitude | longitude |
|------|---------|------------|----------|-----------|
| Guadalajara | Mexico | 1500800 | 20.659699 | -103.349609 |
| Toronto | Canada | 2795060 | 43.653226 | -79.383184 |
| Houston | United States | 2195914 | 29.760427 | -95.369803 |
| New York | United States | 8405837 | 40.712784 | -74.005941 |
| Philadelphia | United States | 1553165 | 39.952584 | -75.165222 |
| Havana | Cuba | 2106146 | 23.05407 | -82.345189 |
| Mexico City | Mexico | 8555500 | 19.432608 | -99.133208 |
| Phoenix | United States | 1513367 | 33.448377 | -112.074037 |
| Los Angeles | United States | 3884307 | 34.052234 | -118.243685 |
| Ecatepec de Morelos | Mexico | 1742000 | 19.601841 | -99.050674 |
| Montreal | Canada | 1717767 | 45.501689 | -73.567256 |
| Chicago | United States | 2718782 | 41.878114 | -87.629798 |

---

## Tasks & Solutions

---

### Task 1 — List all the Canadian cities and their populations

```sql
SELECT city, population FROM north_american_cities
WHERE country = "Canada";
```

**Output:**

| city | population |
|------|------------|
| Toronto | 2795060 |
| Montreal | 1717767 |

---

### Task 2 — Order all the cities in the United States by their latitude from north to south

```sql
SELECT city, latitude FROM north_american_cities
WHERE country = "United States"
ORDER BY latitude DESC;
```

> Highest latitude = furthest north, so we sort `DESC`.

**Output:**

| city | latitude |
|------|----------|
| Chicago | 41.878114 |
| New York | 40.712784 |
| Philadelphia | 39.952584 |
| Los Angeles | 34.052234 |
| Phoenix | 33.448377 |
| Houston | 29.760427 |

---

### Task 3 — List all the cities west of Chicago, ordered from west to east

```sql
SELECT city, longitude FROM north_american_cities
WHERE longitude < -87.629798
ORDER BY longitude ASC;
```

> Chicago's longitude is `-87.629798`. More negative longitude = further west, so we filter `< -87.629798` and sort `ASC` (most negative first = westernmost first).

**Output:**

| city | longitude |
|------|-----------|
| Los Angeles | -118.243685 |
| Phoenix | -112.074037 |
| Guadalajara | -103.349609 |
| Mexico City | -99.133208 |
| Ecatepec de Morelos | -99.050674 |
| Houston | -95.369803 |

---

### Task 4 — List the two largest cities in Mexico (by population)

```sql
SELECT city, population FROM north_american_cities
WHERE country = "Mexico"
ORDER BY population DESC
LIMIT 2;
```

**Output:**

| city | population |
|------|------------|
| Mexico City | 8555500 |
| Ecatepec de Morelos | 1742000 |

---

### Task 5 — List the third and fourth largest cities (by population) in the United States and their population

```sql
SELECT city, population FROM north_american_cities
WHERE country = "United States"
ORDER BY population DESC
LIMIT 2 OFFSET 2;
```

> `OFFSET 2` skips the top 2 (New York, Los Angeles), then `LIMIT 2` returns the next two.

**Output:**

| city | population |
|------|------------|
| Chicago | 2718782 |
| Houston | 2195914 |

---

## Key Takeaways

- Filtering with `WHERE country = "…"` isolates rows by a specific string value
- Sorting by `latitude DESC` gives north-to-south order; `longitude ASC` gives west-to-east
- `LIMIT` + `OFFSET` together enable pagination — skip the top N results and grab the next batch
- All clauses can be combined freely: `WHERE` → `ORDER BY` → `LIMIT` → `OFFSET`
