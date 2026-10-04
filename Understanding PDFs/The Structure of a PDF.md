
https://medium.com/@jberkenbilt/the-structure-of-a-pdf-file-6f08114a58f6

https://tools.town/learn/developer-tools/binary-encoding-guide/

https://en.wikipedia.org/wiki/UTF-8

- The inside of a PDF
	- think of opening a PDF with a text editor rather than a PDF reader
	- a PDF is an **indexed collection of objects**
		-  a PDF **object** is a chunk of structured data
		- the PDF **file** consists of the header, the definitions of various objects, a **cross reference table**, and then a trailer
			- a PDF **cross reference table** is a lookup table providing the location of each numbered object as a byte offset within the PDF
				- a **lookup table** is used to save computation by acting as an array of precomputed values 
				- A **byte offset** is the distance measured in bytes from the beginning of a data structure, such as an array or file, to a specific element or point within that structure. It is used to locate data efficiently in memory or during file operations.
	- you need to be able to search inside a PDF for the byte-offset to be useful
		- you have to be able to go straight to a part of the PDF you want without going through the whole thing 

- When a PDF is opened, a reader starts by going to the end of the file, because at the end of the file is the byte offset to the cross reference table
	- the cross reference table contains the location of each object within the PDF in addition to a **trailer dictionary** which contains the object number of the **document catalog**
		-  a **document catalog** contains a variety of information about the document, such as annotations, thumbnails, etc.
	- the most important object in the PDF is the **pages tree**, which is used to find specific pages

	- the first number you see at the top ofa PDF is the **object number** while the second is the **generation** and is usually 0. The body of the object is everything up until **endobj**


- you should be able to install qpdf and jq from a given app repo vs building it from source

- an editor that encodes a PDF using UTF-8 will break the PDF
	- text encoding for the web - nearly every web page will use UTF-8
	- 


- A minimal PDF
```

|%PDF-2.0|
|1 0 obj|
|<<|
|/Pages 2 0 R|
|/Type /Catalog|
|>>|
|endobj|
|2 0 obj|
|<<|
|/Count 1|
|/Kids [|
|3 0 R|
|]|
|/Type /Pages|
|>>|
|endobj|
|3 0 obj|
|<<|
|/Contents 4 0 R|
|/MediaBox [ 0 0 612 792 ]|
|/Parent 2 0 R|
|/Resources <<|
|/Font << /F1 5 0 R >>|
|>>|
|/Type /Page|
|>>|
|endobj|
|4 0 obj|
|<<|
|/Length 44|
|>>|
|stream|
|BT|
|/F1 24 Tf|
|72 720 Td|
|(Potato) Tj|
|ET|
|endstream|
|endobj|
|5 0 obj|
|<<|
|/BaseFont /Helvetica|
|/Encoding /WinAnsiEncoding|
|/Subtype /Type1|
|/Type /Font|
|>>|
|endobj|
||
|xref|
|0 6|
|0000000000 65535 f|
|0000000009 00000 n|
|0000000062 00000 n|
|0000000133 00000 n|
|0000000277 00000 n|
|0000000372 00000 n|
|trailer <<|
|/Root 1 0 R|
|/Size 6|
|/ID [<42841c13bbf709d79a200fa1691836f8><b1d8b5838eeafe16125317aa78e666aa>]|
|>>|
|startxref|
|478|
|%%EOF|
```


- the above outputs "Potato" if you convert the text file into a PDF