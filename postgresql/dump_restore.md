# Dump and restore scripts
## Local Machine
### First variant
```
# Dump DB
pg_dump -Fc database > database.dump
# Create empty DB
createdb database_from_dump

# Restore with different role as owner
pg_restore --no-owner --role=your_role -d database_from_dump -n public database.dump
```

### Second, more simple
```
# Dump DB
pg_dump database -O -x > dump.sql

# Create empty DB
createdb database_from_dump

# Restore with current user as owner
psql database_from_dump < dump.sql
```
## Backup remote database

```
pg_dump --dbname=postgresql://[USER]:[PASSWORD]@[HOST]:[PORT]/[DATABASE_NAME] --file=dDATABASE_NAME_DUMP.sql
```
