---
---
It's possible to load your Django app after changing some static files settings - such as adding an S3 bucket to the back end - and lose the traditional grid lines and other style elements of the page:

![[./_resources/When_Django_REST_page_loses_its_styling.resources/unknown_filename.png]]

I'm coming back to this question a bit late, but I believe the solution involves checking where static files - such as the background and other formatting - are stored.
