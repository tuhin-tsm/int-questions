### IS NULL

When selecting rows with a where clause, use IS NULL to add null rows to the selection.

```sql
SELECT name FROM Customer
WHERE referee_id != 2 OR referee_id IS NULL
```

### `DISTINCT` and `GROUP BY`

Both `DISTINCT` and `GROUP BY` can be used to achieve similar results, such as eliminating duplicate rows.

However, in practice, `DISTINCT` is often faster than `GROUP BY` for several reasons:

1. Intent and Execution Plan:

`DISTINCT`: The primary intent is to remove duplicates. The database engine typically uses sorting or hashing to identify and remove duplicates.
`GROUP BY`: The intent is to group rows based on the specified columns, which often involves more complex operations like aggregations (e.g., COUNT, SUM). Even if no aggregation is specified, the engine prepares for potential aggregation.

2. Simpler Operations:

`DISTINCT`: It performs a single operation of deduplication. After sorting or hashing, duplicates are simply removed.
`GROUP BY`: It involves grouping rows and possibly performing aggregate functions. Even without aggregates, the grouping operation is more complex than simple deduplication.
