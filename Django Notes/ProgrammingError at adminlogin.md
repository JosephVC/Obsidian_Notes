---
---
![[./_resources/ProgrammingError_at_adminlogin.resources/unknown_filename.png]]

1.18.21

Clearly this is a database issue.  **This works locally**, so is clearly a Heroku issue.

Trying to delete the database and the migrations in the 'users' app did not work; the same issue was encountered after pushing new code to Heroku and trying to run migrations on the heroku end

**SOLUTION**

go into the database in Heroku and **Reset** the database:

![[./_resources/ProgrammingError_at_adminlogin.resources/unknown_filename.1.png]]

Then run **heroku run python manage.py migrate**
