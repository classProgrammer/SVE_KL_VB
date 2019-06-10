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
  
## REST Entwurf
  - Festlegen des Objektmodells
  - Modellierung der URIs
  - Definition der Datenformate
  - Definition der Semeantik der Methoden
  
# Advanced Concepts
  
## Rest Maturity Model (RMM)  
   - Level 3: HATEOS
     - Durch Verfolgen von Links durchwandert der Client verschiedene Zustände der Anwendung
     - Ressourcen repräsentieren Zustände, Links mögliche Transitionen ("Automat")
     - PRO: 
       - Client muss nicht angepasst werden da die Möglichkeiten der Resource mitgeschickt werden (Links)
       - Server kann einfach neue Funktionalität hinzufügen
   - Level 2: HTTP-Methoden
     - GET, POST, UPDATE, ... werden verwendet
     - Statuscodes werden verwendet
     - HTTP-Header werden verwendet
   - Level 1: Ressourcen
     - mehrere Endpunkte
     - Resourcen haben ID
     - Operationen auf Resourcen
     - Möglichkeiten von HTTP immer noch nicht ausgeschöpft 
   - Level 0: Remote Procedure Calls 
     - HTTP wird nur zum Transport verwendet
     - mit SOAP vergleichbar

## HAL Hypertext Application Language
  Foramt um links zu realiseiren z.B. HAL+JSON und HAL+XML
  
  
## Rest mit Spring
  - Domain Class = POJO
  - @RestController
  - @RequestMapping(value="/user/{id}", method=RequestMethod.GET)
  - @GetMapping (value="/employees?start={start}&size={size}"), @PostMapping
  - @RequestParam => start in "/employees?start={start}&size={size}"
  - @RequestBody
  - @PathVariable => id in "/user/{id}"
  - @ResponseBody
  - ResponseEntity
```Java
  @ResponseStatus(HttpStatus.NOT_FOUND)
  public class EmployeeNotFoundException extends RuntimeException{}
```
  
## Content Negotiation
  - einschränkung der möglichen Typen 
    - produces=MediaType.APPLICATION_JSON_VALUE
    - consumes=MediaType.APPLICATION_XML_VALUE
    
  
