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

Some documentation on google financial api may be found on the [unofficial documentation](http://www.networkerror.org/component/content/article/1-technical-wootness/44-googles-undocumented-finance-api.html).

## News 

### Twitter

This directory all the stuff related to twitter ingestion :
* A generic feed to ingest twitter news .  
* A generic feed to ingest twitter news related to google. 

Concerning the getTwitter processus make sure the clock on the sandox and the host are ok. 

`yum install -y ntp`
`service ntpd stop`
At home use `ntpdate pool.ntp.org` 
At teradata office use `ntpdate -vd time01.teradata.com`
You may also set those two adress in the file `/etc/ntp/step-tickers`
`service ntpd start`

Use `time01.teradata.com`



### Yahoo News 
To be defined.

### Financial Times 
To be defined.


## Kibana 

Elastic is already installed in Kylo (port __9200__ and port __9300__).
In order to have a description of your index you may use the curl command : `curl -XGET 'localhost:9200/_cat/indices?v&pretty' `.


In order to setup Kibana you should follow [this tutorial ](https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-centos-7), main steps are : 
* Downlaod and install Kibana as a service.
* use Nginx as a reverse proxy. 

You could use the port __8989__ for kibana. 

In the configuration file, instead of using __example.com__  you may use __sandbox.kylio.io__.






## Documentation 

In order to update this document you may use this [markdown-cheatsheet](https://github.com/tchapi/markdown-cheatsheet/blob/master/README.md).
