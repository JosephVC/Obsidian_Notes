---
---
the following line uses tick marks (\` \`) to denote a line:
app.listen(port, () \=> console.log(\`server started on port ${port}\`));

this produces the output:
![[./_resources/Difference_between_literals_-_single_quotes,_double_quotes,_back_tick_marks.resources/unknown_filename.png]]

the same line of code using single quote marks (' ') . . . 
app.listen(port, () \=> console.log('server started on port ${port}'));

produces the following:

![[./_resources/Difference_between_literals_-_single_quotes,_double_quotes,_back_tick_marks.resources/unknown_filename.1.png]]

double quotes produces the same output as the above

**WHY?!?!**

There are differences in **literals** 

**Object literals =** { }
**Boolean literals =**  true, false
**String literals =** ' ', " "
**Template literals =** \` \` (back tick character)

The use of **template literals** allow cleaner code in some circumstances and a wider array of expression when creating what would otherwise be strings:

![[./_resources/Difference_between_literals_-_single_quotes,_double_quotes,_back_tick_marks.resources/unknown_filename.4.png]]
produces:
![[./_resources/Difference_between_literals_-_single_quotes,_double_quotes,_back_tick_marks.resources/unknown_filename.3.png]]

and ![[./_resources/Difference_between_literals_-_single_quotes,_double_quotes,_back_tick_marks.resources/unknown_filename.5.png]]

produces:
 ![[./_resources/Difference_between_literals_-_single_quotes,_double_quotes,_back_tick_marks.resources/unknown_filename.2.png]]

You can also use the template literals to allow a wider variety of expression when declaring variables:

![[./_resources/Difference_between_literals_-_single_quotes,_double_quotes,_back_tick_marks.resources/unknown_filename.6.png]]

![[./_resources/Difference_between_literals_-_single_quotes,_double_quotes,_back_tick_marks.resources/unknown_filename.7.png]]

or 

![[./_resources/Difference_between_literals_-_single_quotes,_double_quotes,_back_tick_marks.resources/unknown_filename.8.png]]
