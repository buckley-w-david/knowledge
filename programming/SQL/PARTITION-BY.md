# Common Table Expressions + PARTITION BY

I can never remember the syntax of these things.

```sql
WITH 
    Records AS (
        SELECT 
            col1,
            ROW_NUMBER() OVER (
                PARTITION BY col2 
                ORDER BY col3 DESC
            ) row_num,
          FROM table T
        )

SELECT *
FROM Records
WHERE row_num < 2
```

This will give you the top 1 record (based on col3) for each group made by col2
