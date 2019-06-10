# SOA and Microservices

## Definition of a Service
  Ein Service ist eine slebstverwaltende Instanz die zur gänze eine Aufgabe in vollem Umfang (von der DB-Kommunikation bis zur Schnittstelle z.B. REST) übernimmt und aus mehreren Services bestehen kann. Der Consumer weis nichts über die interne Struktur und verwendet nur den Endpoint.
  
  - Is a logical representation of a repeatable business activity that has a specified outcome (e.g., check customer credit; provide weather data, consolidate drilling reports)
  - Is self contained
  - May be composed of other services
  - Is a “black to consumers of the service   
  
## Komponenten und Services
  - Eine Komponente ist eine Softwareeinheit welche
    - eine klar definierte Schnittstelle aufweist,
    - unabhängig verwendbar,
    - austauschbar und
    - aktualisierbar ist
  - Bibliotheken sind Komponenten, die
    - sich im selben Adressraum wie das Hauptprogramm befinden und
    - über Funktions bzw. Methodenaufrufe angesprochen werden.
  - Services sind Komponenten, die
    - als eigenständige Prozesse ausgeführt werden und
    - über Service Requests oder entfernte Funktionsaufrufe angesprochen werden.
    
## Definition Serviceorientierte Architektur (SOA)
“SOA is an application architecture in which all functions, or services, are
defined using a description language and have invokable interfaces that are
called to perform business processes . Each interaction is independent of each
and every other interaction and the interconnect protocols of the communi
cating devices (i.e., the infrastructure components that determine the
communication system do not affect the interfaces). Because interfaces are
platform independent , a client from any device using any operating system in
any language can use the service.”

## Eigenschaften von Services
  - Explizite Service-Kontrakte
    - die exportierte Funktionalität wird bekannt gegeben
  - Lose Kopplung
    - Services sind unabhängig voneinander
    - Async (MOM) oder Sync (REST/SOAP) Nachrichtenaustausch
  - Services sind autonom
    - Implementierungsdetails sind vollständig verborgen
    - Client ist unabhängig von Service-(Laufzeit)Umgebung/Sprache/Bibilotheken
    - Services sind fehlerresistent
  - Anwendungsbezogenheit
    - Services realisieren Geschäftsfälle der Anwendungsdomäne.
  - Interoperability
    - verschiedene Sprachen
    - Standardprotokolle werden verwendet z.B. HTTP
  - Stateless
    - kennt nur sich slebst
    - Skalierbar, Verteilbar
  - Auffindbarkeit
    - eindeutige Adresse URI
  - Aggregierbarkeit
    - Zusammenschluss von Services mittels Orchestrierung bzw. Choreographie.
    
 ## Orchestrierung
  - zentrale Verwaltung von Services
  - CONTRA:
    - Singel Point of Failure
    - Enge Kopplung von Services
    
 
