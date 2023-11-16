# Text


---
### Notes and Ideas:
- Representing text in a computer
	- Bits and Bytes:
		
- Text file encoding and text formats 
- ASCII American Characters
- Unicode:
	- def: Standard character encoding system that assigns a unique number to every character for any
	- chr() function in python converts
- UFT-8:
	- Character encoding format that can represent any character in the unicode standard 
	- it's the default encoding format
	- in python encoding = 'utf-8'
- Format followed by the characters:
	- CSV
	- XML
		- designed to store and transport data 
		- XML was designed to be both human and machine readable 
		- similar to HTML
		- structures:
			- root element( the starting of the XML) -- must have 
			- child elements(branches from the root)
			- sub elements ( all elements can have sub elements)
		- All XML elements must have a closing tag
		- 
		- parse xml with python:
			- X path 
				- XML path language
				- XPATH use "path like" sysntax to identify and navigate ndoe sin XML and HTML documents
				- 
			```
			Element.findall() #finds only elements with a tag
			 ```

	- HTML
		- 
	- JASON
	- Natural Language text
	- programing languages
	- non-text based formats: mp3, png, jpg...
- XML vs HTML:
	- XML was designed to carry data - with focus on how to transfer data
	- HTML was designed to display data - with focus on how data looks
```
# some format have much overhead;
ls -lh(human readable)
# 
```

---
### Bag of words:
1. Tokenization:
2. Remove stop words
3. Building the vocabulary:
	1. construct a vocabulary or a set of unique words from the tokenized documents
	2. Each word in the vocabulary is assigned a unique words from the tokenized documents
	3. each word in the vocabulary is assigned a unique index or identifier
4. Document Representation: represent each document in the corpus using a feature vector:
	1. The feature vector has a fixed length equal to the size of the vocabulary
	2. each element in the feature vector reprsents the count of frequency of the corresponding word in the document 
---
TF-IDF(Term Frequency-Inverse Document Frequency):
- measure the importance of terms in a document corpus
- 
- it combines two concepts:
	- term frequency(TF):
		- Measures the occurrence of a  erm in a document.
		- It is calculated as the ratio of the  number of times a term appears in  a document to the total number of  terms in the document.
		- TF helps identify the most frequent  terms in a document
		- TF(t, d) = count(t, d)/len(d)
	| t:term/word/token| d: document | count(t,d): number of times  t is in d| len(d): number of terms in d|

	- inverse document frequency(IDF):
		- Measures the rarity of a term across  the entire document corpus
		- It is calculated as the logarithm of the  ratio between the total number of  documents in the corpus and the  number of documents that contain the  term.
		- IDF helps identify the most important terms that are relatively rare across  the corpus.


---

### Key words:
[[regular expressions With REgEX Module in Python]]
---
#### TAGS