---
---
**Bind Parameters**

Bind parameters are where SQL and JavaScript collide; this is where the whole use of **exec()** comes from

![[./_resources/Untitled_Note.15.resources/sql - basic bind patterns.png]]

another way to use SQL and Javascript is to use a question mark, which tells SQL that the programmer will be providing a parameter

![[./_resources/Untitled_Note.15.resources/sql - bind patterns - question mark.png]]

You can  use more than one ? to specify multiple parameters you want selected; each instance of **?** need to be filled/referred to

![[./_resources/Untitled_Note.15.resources/sql - bind patterns - question mark - multiple par.png]]

If the refer to the wrong item, you get \[  \] in return

![[./_resources/Untitled_Note.15.resources/sql - bind patterns - question mark - multiple par.1.png]]
