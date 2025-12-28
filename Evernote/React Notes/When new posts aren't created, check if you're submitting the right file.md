---
---
![[./_resources/When_new_posts_aren't_created,_check_if_you're_submitting_the_right_file.resources/unknown_filename.png]]

In the above code, only PDF files are accepted.  These types of posts are likely to be accepted (if every other parameter for a successful post is made) but if an image file is uploaded - which is not supported by the code above - you'll get "**OPTIONS /api/ HTTP/1.1" 200 0** response, meaning nothing really happened

The above being said, when a new post was actually made the back end coughed up a bunch of odd-looking errors:

![[./_resources/When_new_posts_aren't_created,_check_if_you're_submitting_the_right_file.resources/unknown_filename.1.png]]

On the JS side, this error pops up when submitting a pdf:
![[./_resources/When_new_posts_aren't_created,_check_if_you're_submitting_the_right_file.resources/unknown_filename.2.png]]
