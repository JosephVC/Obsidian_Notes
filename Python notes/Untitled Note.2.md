---
---
**Python Lists**

#Examples of lists in python

x = \[\]
print (x)
\>>>\[\]  #this is console output
x.append(1)
x
\>>>\[1\]
x.append(2,3,4)   #this will not work, as .append() only takes one argument
y = \[2,3,4\]
x.append(y)
x
\>>>\[1, \[2,3,4\]\]
q = (7,8,9)
x.append(q)
x
\>>> \[1, \[2,3,4\], (7,8,9)\]
r =  \[1,1,1,
      2,2,2,
      3,3,3\]
r
\>>>\[1,1,1,2,2,2,3,3,3\]
