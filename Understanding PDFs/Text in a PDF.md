
all from the jberkenbilt Medium articles

**Transformation Matrices**
- a PDF will use linear transformations on graphics and text using **transformation matrices** 
	- this is basically  used to scale text and other objects
	-  both the text and graphics transformation matrix are expressed in the form of six numbers
	- when the matrices are used to scale and position things, the numbers represent
		- horizontal scale factor
		- zero
		- zero
		- vertical scale factor
		- horizontal position relative to left edge
		- vertical position relative to bottom edge



- the basic unit of measurement in the PDF is the Point, which is 1/72 of an inch; the same unit is used in printing and word processing, generally


- the **origin** of the PDF is the bottom left corner of the page, so to move down the page you need negative offsets

**- text layout operators**
	- there are a variety of text layout operators, but here are two examples
		- hs 0 0 vs x y Tm : The Tm operator sets the text transformation matrix as described
			above, where hs and vs are the horizontal and vertical scale factors and x and y are
			the horizontal and vertical location of the position where the next piece of text will be displayed.
		-  dx dy Td : The Td operator moves the current text position to the right by dx points and up by dy points relative to the beginning of the previous line. Note that dy moves up, so we typically see negative values for dy . Note also that Td sets the position of the line relative to the beginning of the previous line, not relative to current position, which and means Tmthe operators parameters set the to text Td are position independent and the of position the text of of the the current previous line. 

- pdf operators follow their parameters
	- if you have the text field "(cat) Tj"  the string cat is the operator and the parameter is Tj
		- in Postscript, you have operators following their operands


**Text Display Operators**
- the two main text display operators are **Tj** and **TJ** 
- operator names are case sensitive
- **Tj** shows a single string of text at the current text position and advances the position by the width of the text
- **TJ** takes an array of strings and numbers and handles them sequentially; if it is dealing with a string, it displays the string at the current position and the advances that position by width of the string just like **Tj** would
	- when dealing with a numbers, the text position is moved in the opposite direction of the text flow
		- it does this by measuring in units that are 1/1000th of the current font size
		- [(T) 80 (wo)] would move the "wo" .08 times the font size to the left (80/1000th of the font size) when writing "Two"
- **kearning** involves making fine adjustments to text position to improve the visual appearance of text. high quality fonts will often include **kearning tables** to specify these sorts of adjustments. 
- **Justification** - creating even text margins - is also a use of this


**Graphics Operators**
	- the graphics state of a PDF contains things like clipping region, current color, fill pattern, transformation matrix, line width, etc.
	- the operators **q** and **Q** isolate changes to the PDF graphics state by saving and restoring the graphics state


**Character Encodings**
- also called a **coding system** 
- provides a numeric value to each character - this value is called a **code point**
	- an example is ASCII, where every character on a standard US keyboard has a value between 0-127
	- UNICODE tries to have a character encoding for every character in languages around the world
- coding system is set up as a sequence of bytes
	- ASCII uses a byte per character, up to 256 bytes - a **single byte** coding system
	- several other single byte encodings extend ASCII by assigning other characters to the values between 128 and 255
		- one of these is the **PDF Doc Encoding**
		- there are also PC and Mac specific character encoding systems also included in PDF


**Unicode, UTF - 8/16**
- Unicode has over a million valid code points, thus it often takes more than one bytes to represent many of these characters
- In Unicode, collections of related characters are divided into planes
	- **basic multilingual plane**
		- encodings from 0 to 65, 535 that covers all characters used in global written languages, including special characters and symbols
			- what is not considered "basic" is emoji, musical notation, etc.
	- PDF uses the **big endian UTF-16** encoding (UTF-16-BE)
		- each character in the basic multilingual plane is represented as a two-byte sequence consisting of four hexidecimal digits  representing the hex Unicode code point
			- "A" has ASCII value 41, where the decimal value is 65
				- in UTF-16-BE, that value is 0041
				- characters with higher codes are represented as four byte pairs of two byte values known as **surrogate pairs**
		- the little or big endian issue regards how CPUs order bytes
			- Intel CPUs represent large numerical values in little endian order while ARM and Motorola CPUs are big endian
		- **endianness** regards the byte order of a (computing) **word** 
			- basically, do you start at the big end of the word or the little end?
			- **big endian** -  orders by a decreasing numerical significance with increasing memory addresses
			- **little endian** - orders by increasing numerical significance with increasing memory addresses
			- ![[Pasted image 20261115115803.png|572]]
	