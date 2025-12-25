---
---
**raise InconsistentMigrationHistory(**
**django.db.migrations.exceptions.InconsistentMigrationHistory: Migration admin.0001\_initial is applied before its dependency users.0001\_initial on database 'default'.**

this arose after I created a new **users** app which created custom  user settings . My brute force solution was to delete the **db.sqlite** database and run **makemigrations** and **migate** all over again
