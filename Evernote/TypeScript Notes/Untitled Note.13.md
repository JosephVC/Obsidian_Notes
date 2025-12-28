---
---
**Type keyword**

we can declare our own types using the **type** keyword **\-  type MySringType = string**

if you declare a type as a string, like the above you need to keep using it as a string

you can also effectively connect types by assigning new types to what you've declared before 

![[./_resources/Untitled_Note.13.resources/typescript - type keyword.jpg]]

while typescript programs are valid javascript programs, the type issue is the exception.  after checking types, the Typescript compiler generates JavaScript by removing all typescript-specific syntax,  then the result is run as JavaScript

the fact that typescript types are tossed out is important because when  you have a simple enough Typescript statement, that will eventually be removed when being converted to JS, thus leaving an **undefined** value - this is called **type erasure**

![[./_resources/Untitled_Note.13.resources/typescript - types tossed out.jpg]]
