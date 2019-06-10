# Advanced REST

## REST Concepts, The 5 Architecture Concepts of the Web (REpresentation State Transfer)
  - Addressable Resource: URI for resources
  - Uniform Constrained Interface: limited number of ops (POST, GET, PUT, DELETE, UPDATE)
  - Representation-Oriented: different representations (JSON, XML, YAML)
  - Communicate Statelessly: requests know nothing
  - HATEOS - Hypermedia As The Engine Of Application State: Resourcen enthalten links auf mögliche Operationen
  
## SOAP
  - operation oriented
  - interfaces with lots of methods
  - Zerlegung der Methoden in Anfrage- und Antwortdokument
  - Serialise in- and outputparams
  
## REST
  - resource oriented
  - exchange of resources between client and server
  - predefined operations are eecuted on the resources
  - exchange of resources via HTTP-request and -response
  - Abbildung der operationen auf HTTP
  
## Uniformd Constrained Interface
  PRO:  
  - Einfach, leicht zui verstehen, kaum Metadaten notwendig, keine Proxies oder komplexe Client Bibliotheken notwendig
  - Interoperability: HTTP-Client ist genug, keine Hersteller Probleme
  - Skalierbarkeit: Caching, ...
 
## Representation Oriented
  - nicht standardisiert (SOAP => standardisiert)
  - XML, JSON und YAML sind verbreitete Formate
  - HTTP-Header Content-Type => Content Negotiation
  - Austausch via HTTP
  
