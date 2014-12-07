---
layout: post
title: Verbreitung von Formica sanguinea
---

Mit dem freien Statistikpaket R ist es möglich, die Datenbank von [GBIF](http://www.gbif.org/) (Global Biodiversity Information Facility) abzufragen. 
Dies ist mit dem Paket spocc möglich, daß von [ropensci](http://ropensci.org/) zur Verfügung gestellt wird. Der R-Code zum Abfragen des Vorkommens 
der Ameisenart Formica sanguinea lautet z.Bsp. folgendermaßen:

{% gist HansNovak/ca87024a501c5eac7655 gbif_formica_sanguinea.R %}

Alternative Codedarstellung:

{% highlight R linenos %}

# load library spocc
library(spocc)
 
# query GBIF for georeferenced occurrences of the ant species Formica sanguinea 
df <- occ(query = 'Formica sanguinea', from = 'gbif', gbifopts = list(hasCoordinate = TRUE))
 
# list the first six datarows and first four columns
head(df$gbif$data$Formica_sanguinea[, 1:4])
 
# display the records on a dynamic map created with the library Leaflet
mapleaflet(data = df, dest = ".")
 
# display the records on a static map created with the Google API
mapggplot(df)

{% endhighlight %}

