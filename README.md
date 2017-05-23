# kylo-demo

## Company

The campany directory is composed of a feed and some file to ingest. 
* The template should be imported in Kylo : [compagnies.feed.zip](stocks/compagnies/feed/compagnies.feed.zip ) (Feed => + => Import File ) 
* A file to ingest with the list of the company : [compagnies.csv](stocks/compagnies/input/compagnies.csv )
* A sample to use when creating the feed : compagnies-sample.csv  [compagnies.csv](stocks/compagnies/input/compagnies-sample.csv) 


## Stocks
Concerning the stock , you should import the tempalte in Kylo and then create a feed. The directory contains the following files 
* The template you should use : [quoteTemplateForIngest.xml](stocks/quotes/quoteTemplateForIngest.xml )
* The the files that should be imported  [getprices.goog.txt](stocks/quotes/input/02_fileToIngest/getprices.goog.txt ).

In case you would like to recreate a file you should use the following request : 
https://www.google.com/finance/getprices?q=MMM&i=86400&p=40Y&f=d,c,v,k,o,h,l&df=cpct&auto=0&ei=Ef6XUYDfCqSTiAKEMg

Note that if you want the last quote from the day you should use the following request : 
https://www.google.com/finance/getprices?q=GOOG&i=86400&p=2d&f=d,c,v,k,o,h,l&df=cpct&auto=0&ei=Ef6XUYDfCqSTiAKEMg


## News 

### Twitter

This directory all the stuff related to twitter ingestion :
* A generic feed to ingest twitter news .  
* A generic feed to ingest twitter news related to google. 

### Yahoo News 
To be defined.

### Financial Times 
To be defined.

