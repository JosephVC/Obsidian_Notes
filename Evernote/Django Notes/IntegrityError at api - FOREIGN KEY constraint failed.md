---
---
![[./_resources/IntegrityError_at_api_-_FOREIGN_KEY_constraint_failed.resources/unknown_filename.png]]

In this case, we have **author** and **category** models, and the later needs to be be populated.  The solution is to go into the admin panel as a superuser and create a category.  We need a the **category** field already filled in because the default value of the model is set to 1, meaning the code expects at least one instance of the model to already be there:
        category = models.ForeignKey(
        Category, on\_delete\=models.PROTECT, default\=1
    )
