---
---
![[./_resources/Poetry_Not_Seeing_Your_Python_Install.resources/unknown_filename.png]]

the error above gives a path to the env that is causing trouble, which lives here

![[./_resources/Poetry_Not_Seeing_Your_Python_Install.resources/unknown_filename.1.png]]

Track down and delete that env, then recreate it with **poetry add \[preferred software package\]** 

Another option is to type **poetry remove django** and then **poetry add** django back in
