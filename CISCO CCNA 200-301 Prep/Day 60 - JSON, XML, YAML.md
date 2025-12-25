---
---
**Data Serialization**

* the process of converting data into a standardized format/structure that can be stored in a file or transmitted over a network and reconstructed later by the same or different applications
	* this allows data to be communicated between applications in a way both applications understand
* data serialization languages allow us to represent variables with text
* ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.png]]

**JSON (JavaScript Object Notation)**

* an open standard and data interchange format that uses human-readable text to store and transmit data objects
* it is standardized in RFC 8259
* it was derived from JavaScript, but it is language-independent and many modern programming languages are able to generate and read JSON data
	* REST APIs often use JSON
* Whitespace is insignificant
* JSON can represent four **primitive data types**
	* string: surrounded by double-quotes ("hello")
	* number: just a number
	* boolean: true or false value
	* null: intentional absence of any value
* JSON also has two structured data types
	* object
		* sometimes called a **dictionary**
		* unordered list of **key-value pairs (variables)**
			* objects are surrounded by curly brackets {}
			* the **key** is a **string**
			* the **value** is any valid JSON data type (see above)
			* the key-value pair are separated by a colon
			* if there are multiple key-value pairs, each pair is separated by a comma
			* ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.1.png]]
			* objects are a valid data type for the value of a key-value pair
				* ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.2.png]]
				
	* array
		* a series of **values** separated by commas
			* **not** key-value pairs
			* the values don't have to be in the same data type
			* ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.3.png]]

* ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.4.png]]

**XML**

* **Extensible Markup Language**
	* was developed as a markup language, but is now used as a general data serialization language
		* **markup languages** are used to format text
* XML is generally less human-readable than JSON
* **whitespace is not significant** but is added for the sake of readability
* often used by REST APIs
* general **format** of : <key>value</key>
	* ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.5.png]]

**YAML (YAML Ain't Markup Language)**

* originally meant **Yet Another Markup Language**
* YAML is used by the network automation tool Ansible
* human-readable
* **whitespace and indentation are significant**
* YAML files start with "---"
* lists are indicated by "-"
* keys and value are represented by **key:value**
* ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.6.png]]

**QUIZ**

1. ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.7.png]]
	* B

\\

2. ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.8.png]]
	* c

3. ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.9.png]]
	* E

4. ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.10.png]]
	* c
		* there does not need to be a comma after the final "1000"

5. ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.13.png]]

* B

5. ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.11.png]]
	* D

6. ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.12.png]]
	* a

7. ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.14.png]]

* d

8. ![[./_resources/Day_60_-_JSON,_XML,_YAML.resources/image.15.png]]
