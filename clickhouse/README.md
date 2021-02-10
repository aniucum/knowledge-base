- размер таблиц
```bash
SELECT table, round(sum(bytes) / 1024/1024/1024, 2) as size_gb FROM system.parts WHERE active GROUP BY table ORDER BY size_gb DESC
```
