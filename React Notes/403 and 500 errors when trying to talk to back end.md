---
source: https://app.slack.com/client/T03LJKBP8/D9LDFFSKC
---
![[./_resources/403_and_500_errors_when_trying_to_talk_to_back_end.resources/unknown_filename.png]]

For the above, the relevant django view is set to **IsAuthenticated**, which in this case is blocking React from loading the posts I need it to

**SADLY** there is another error when I set the view permissions to be more lax: 

![[./_resources/403_and_500_errors_when_trying_to_talk_to_back_end.resources/unknown_filename.1.png]]

The above is tied to the following back end error:

![[./_resources/403_and_500_errors_when_trying_to_talk_to_back_end.resources/unknown_filename.2.png]]

Once the back end API is logged out of, the following error immediately pops up in django:

![[./_resources/403_and_500_errors_when_trying_to_talk_to_back_end.resources/unknown_filename.3.png]]

Normally, this was locking me out of my localhost/api/ page, but after creating some new views and URLs, I've gotten access via localhost8000/api/admin/create/ .  This allows me to both log in and gain access to the overall api

Sadly, deleting past migrations - **which does not solve the problem -** has screwed with my overall django admin access, meaning I'll likely create a slug superuser just to gain access.

changing the following method in a major view solved the problem (I think).  this is the offending method:
def get\_queryset(self):
user = self.request.user
return Post.objects.filter(owner=user)

asdf
