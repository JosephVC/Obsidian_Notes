---
source: https://www.executeprogram.com/courses/sql/lessons/null-in-unique-constraints
---
**NULL in Unique Constraints** 

NULL value are ignored by the UNIQUE constraint

because it woudl be possible for  table of, say, users, to have an one unique value for their name but NULL values for some other attribute, the UNIQUE  constraint will ignore NULL.  if it did not, the only one user would allowed a NULL value for a particular field
