---
---
**General Terms**

**#** : this is the 'pound character' used for commenting in python; put that symbol in front of a line and the entire line will be commented out, and not read  as code

**""**: These are quote signs, and whatever goes in between them will be considered a string; triple quotes can be used to create paragraphs of text, with one """ at the top and one at the bottom

**print()**:  This command tells python to print to the screen whatever follows the command; there could be a string in quotes, or some simple addition, or whatever else

**\+ - \* / = ;** : These are all operators that can be used to manipulate both numbers, variables, and strings; strings of text can be added together; the '=' sign can be used when assigning value to variables, such as 'x = 1' or 'x = hello'; the ';' can be used to string multiple lines of code together

**<, >** : greater than or less than; these are used for comparison purposes, as when one is comparing the values of certain variables to see which one is larger or smaller

**%** :  this does several things.  First, it is the modulo operator.  The modulo operator divides two numbers and returns the remainder.  THIS IS NOT THE DIVISION OPERATOR, but rather is usuful to see if things are divisible by a certain number without any remainder.  

Also, the percentage sign is used within strings as a way of assigning variables outside of that string to values  within that string (if that makes any sense); an example is -- "Bill is %d years old." % (10) -- now, not just any letter could be put behind the '%', but rather it depends on whether one is inserting a string or a number; the "%s" is used with strings; it could also be used as the only content between " ", with the various pointers outside the string

**\\n** : This is a line break; when put at the end of a line it forces the string to go to the next line

**\\t** : this is used to create a tab
int(): this defines things you are entering as integers
raw\_input(): this is a function that allows you to input what you want, such as -- x = raw\_input() -- you can put int(raw\_input()); you can also input a string within the parenthesis of the raw\_input() -- raw\_input("How old are you?")
input:  there are various powerful functions the programmer can import into their program
argv: this is an argument variable, which his used to hold arguments passed to the python script

from sys import argv

**open()** :  this open a file in one's working directory; it can take

**.read** :  when you open a file, this attaches to the variable used to open the file, such as -- txt = open(filename) --, where txt.read

**.write** : this is a method that attaches to the variable you used to open the file and allows you to write to it

**.close()** :  this is a method that attaches to the variable used to open the file, and then closes the file
