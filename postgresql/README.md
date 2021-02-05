# knowledge-base

```bash
docker run --rm  -p 5432:5432 -d \
           -e POSTGRES_DB=test \
           -e POSTGRES_USER=postgres \
           -e POSTGRES_PASSWORD=postgres \
           --name postgres11.10 postgres:11.10
```
- extensions
  - list of extensions
```bash
\dx
SELECT * FROM pg_extension;
```
CREATE EXTENSION IF NOT EXISTS pgcrypto;



SELECT crypt('mypass', gen_salt('bf', 4));
