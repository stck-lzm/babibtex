# babibtex
The name is a short for bash bibtex file or article to bibtex file (art2bib).
This script will print bibtex of an article or a book from DOI, ISBN, ArXiv or PMID.

### dependencies
It requires:
* bash (tested with 4.4), 
* wget (tested with 1.19), 
* sed  (tested with 4.5), 
* (coreutils).

### usage
To execute the script give it execute right.  
`chmod +x art2bib`
  
Some tests for fun:  
`./art2bib d 10.1142%2F10409`  
`./art2bib isbn 0323030645`  
`./art2bib a 1108.2700`  
`./art2bib pmid 23150728`  
Those are some random examples.
You can use the first letter or the full name of the reference system.  
  
To make a bib file of your own library, (if you have your pdfs with the important informations between brackets):  
`find -type f -iname '*.pdf' | sed 's/^.*\[//; s/\].*//'`   
Now, the input of the entire library are ready for the script, we will use the while loop to find all the bib files:
`while read i; do art2bib $i ; done < <( find -type f -iname '*.pdf' | sed 's/^.*\[//; s/\].*//' ) > list.bib`  
The file called list.bib is ready !

### todo
Maybe add more reference systems, or make the program find the reference system by itself.
