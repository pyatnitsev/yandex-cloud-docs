---
sourcePath: ru/ydb/ydb-docs-core/ru/core/yql/reference/yql-core/syntax/_includes/select/without.md
sourcePath: ru/ydb/yql/reference/yql-core/syntax/_includes/select/without.md
---
## WITHOUT {#without}

Исключение столбцов из результата `SELECT *`.

**Примеры**

``` yql
SELECT * WITHOUT foo, bar FROM my_table;
```

``` yql
PRAGMA simplecolumns;
SELECT * WITHOUT t.foo FROM my_table AS t
CROSS JOIN (SELECT 1 AS foo) AS v;
```