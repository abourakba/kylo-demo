# kylo-demo 

## Introduction
Stock prediction based on news articles and tweets.

Work is based on the work of [Eliano Marques](ElianoMarques_EconometriaAplicadaEPrevisao.pdf)

## Data ingestion
### Companies

The companies directory is composed of:
* The feed should be imported in Kylo : [companies.feed.zip](data_ingestion/companies/feed/companies.feed.zip ) (Feed => + => Import File ) 
* A file to ingest with the list of the companies : [companies.csv](stocks/companies/input/compagnies.csv )
* A sample to use when creating the feed : [companies-sample.csv](data_ingestion/companies/input/companies-sample.csv)


### Stocks
Concerning the stock, you should import the template in Kylo and then create a feed. The directory contains the following files 
* The template you should use : [quoteTemplateForIngest.xml](data_ingestion/stocks/templates/quoteTemplateForIngest.xml )
* Input file [getprices.goog.txt](data_ingestion/stocks/input/02_fileToIngest/getprices.goog.txt ).

In case you would like to recreate a file you should use the following request :
```
https://www.google.com/finance/getprices?q=MMM&i=86400&p=40Y&f=d,c,v,k,o,h,l&df=cpct&auto=0&ei=Ef6XUYDfCqSTiAKEMg
```

Note that if you want the last quote from the day you should use the following request : 
```
https://www.google.com/finance/getprices?q=GOOG&i=86400&p=2d&f=d,c,v,k,o,h,l&df=cpct&auto=0&ei=Ef6XUYDfCqSTiAKEMg
```
Some documentation on google financial api may be found on the [unofficial documentation](http://www.networkerror.org/component/content/article/1-technical-wootness/44-googles-undocumented-finance-api.html).

### Twitter
This directory all the stuff related to twitter ingestion :
* A [template](data_ingestion/twitter/templates/demo_twitter.template.zip) to ingest twitter news.  
* A [feed](data_ingestion/twitter/feeds/google/google_sentiments.feed.zip) to ingest twitter news related to google. 

---
**WARNING**

Concerning the GetTwitter processor, make sure the clock on the sandbox and the host are synchronized.

---

```
yum install -y ntp
service ntpd stop

//At home use 
ntpdate pool.ntp.org

//At teradata office use
ntpdate -vd time01.teradata.com
```

You may also set these to be automatic:

```
vi /etc/ntp/step-tickers
//write in the file
time01.teradata.com

// setup the service to run automatically
service ntpd start
```
### News

#### NewsAPI
Nifi template for metadata ingestion for news articles is provided with [NewsAPI](https://newsapi.org/).

NewsAPI provides over 70+ sources, for which we query one by one.

Directory composition:
* Template [Template-NewsAPI-Ingest.xml](data_ingestion/news/templates/Template-NewsAPI-Ingest.xml) to query for sources and articles. Input is generated automatically to query NewsAPI about current article sources, then it queries for articles on each source. Output is FlowFiles as an article metadata.

#### Yahoo News 
Service no longer available

#### Financial Times 
Service is not free

## Visualization using Kibana

Elastic is already installed in Kylo (port __9200__ and port __9300__).

If you want to have a description of your index:

```
curl -XGET 'localhost:9200/_cat/indices?v&pretty'
```


To setup Kibana you should follow [this tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-centos-7), main steps are : 
* Download and install Kibana as a service.
* use Nginx as a reverse proxy.

You could use the port __8989__ for kibana. 

In the configuration file, instead of using __example.com__  you may use __sandbox.kylio.io__.


## Documentation 

In order to update this document you may use this [markdown-cheatsheet](https://github.com/tchapi/markdown-cheatsheet/blob/master/README.md).
