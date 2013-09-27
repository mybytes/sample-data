sample-data
===========

Sample "cloud" data exported from the Google/Facebook/Twitter etc accounts of ficticious entity Marty MyBytes.

* `mybytes/` -> contains data in RDFa format as exported by MyBytes toolset
* `native/` -> contains data as downloaded from various services "export my data" tools

## Converting to RDF

The Ruby Linked Data gem can be used to extract the raw RDF data from the RDFa files in the `mybytes/` folder as follows:

* `gem install linkeddata`
* `[~/Projects/mybytes/sample-data/mybytes]$ rm all_data.nt && rdf serialize **/* --output-format ntriples --output all_data.nt`

`all_data.nt` is useful for further processing in LinkedData tools such as Apache Jena