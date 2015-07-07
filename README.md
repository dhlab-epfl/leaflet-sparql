# leaflet-sparql

This web page consists of a very basic **Leaflet webmap** that displays the results of a **Sparql query** on a **Virtuoso endpoint**.

It depends on [Leaflet](http://leafletjs.com/) (webmapping library), [jQuery](https://jquery.com/) (general javascript framework) and [jQueryGeo](http://jquerygeo.com/) (geometry processing library).

It is thought as a base for a more complex web map (multiple/custom queries, editing capabilities, ...).

Demo : http://128.178.21.39:8080/map/


## Notes about Virtuoso

Unlike Strabon, Virtuoso doesn't implement the standard GeoSparql defined by OGC. This means that the Sparql query must be rewritten if the endpoint is not a Virtuoso endpoint.

Unlike Strabon, Virtuoso is unable to serve directly well-formatted GeoJSON to be displayed with leaflet. The following formatting is done to transform Virtuoso's Json response to standard GeoJSON's responses :

- restructure the Json object
- convert the geographical representation from WKT to GeoJSON

This means that that part of the javascript could be dropped if using Strabon.

By default, Virtuoso doesn't allow CORS (cross-origin requests), which makes it impossible to dynamically load data from Javascript (the error looks like `"No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'null' is therefore not allowed access."`). See http://virtuoso.openlinksw.com/dataspace/doc/dav/wiki/Main/VirtTipsAndTricksCORsEnableSPARQLURLs to solve this.