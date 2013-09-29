#### Table of VCards, with columns ?fullName, ?familyName, ?givenName, ?email, ?homeLocality ?homeCountryName 

```
PREFIX vcard:   <http://www.w3.org/2006/vcard/ns#>
PREFIX rdf:     <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT *
WHERE {
  ?resource a vcard:VCard .
  ?resource rdf:type ?type .
  OPTIONAL { ?resource vcard:fn ?fullName . }
  OPTIONAL { ?resource vcard:family ?familyName . }
  OPTIONAL { ?resource vcard:given ?givenName . }
  OPTIONAL { ?resource vcard:email ?email . }
  { SELECT ?address ?homeLocality ?homeCountryName
  	WHERE { 
  		?address rdf:type vcard:Address .
  		?address rdf:type vcard:Home .
  		OPTIONAL { ?address vcard:locality ?homeLocality . }
  		OPTIONAL { ?address vcard:country-name ?homeCountryName . }
  	}
  }
  ?resource vcard:adr ?address .
}
```

gives:
```
{
  "head": {
    "vars": [ "resource" , "type" , "fullName" , "familyName" , "givenName" , "email" , "address" , "homeLocality" , "homeCountryName" ]
  } ,
  "results": {
    "bindings": [
      {
        "resource": { "type": "uri" , "value": "https://twitter.com/MartyBytes" } ,
        "type": { "type": "uri" , "value": "http://www.w3.org/2006/vcard/ns#VCard" } ,
        "fullName": { "type": "literal" , "value": "Marty Bytes" } ,
        "address": { "type": "bnode" , "value": "b0" } ,
        "homeLocality": { "type": "literal" , "value": "London" }
      } ,
      {
        "resource": { "type": "uri" , "value": "https://plus.google.com/110781414661317480490" } ,
        "type": { "type": "uri" , "value": "http://www.w3.org/2006/vcard/ns#VCard" } ,
        "fullName": { "type": "literal" , "value": "Marty Bytes" } ,
        "email": { "type": "literal" , "value": "marty@mybytes.io" } ,
        "address": { "type": "bnode" , "value": "b1" } ,
        "homeCountryName": { "type": "literal" , "value": "California" }
      } ,
      {
        "resource": { "type": "uri" , "value": "http://www.facebook.com/marty.bytes" } ,
        "type": { "type": "uri" , "value": "http://www.w3.org/2006/vcard/ns#VCard" } ,
        "fullName": { "type": "literal" , "value": "Marty Bytes" } ,
        "email": { "type": "literal" , "value": "marty@mybytes.io" } ,
        "address": { "type": "bnode" , "value": "b2" } ,
        "homeLocality": { "type": "literal" , "value": "London" } ,
        "homeCountryName": { "type": "literal" , "value": "United Kingdom" }
      }
    ]
  }
}

```

#### Graph of VCards
```
PREFIX vcard:   <http://www.w3.org/2006/vcard/ns#>

DESCRIBE *
WHERE {
  ?resource a vcard:VCard .
}
```

#### List all triples

```
SELECT * {?s ?p ?o}
```