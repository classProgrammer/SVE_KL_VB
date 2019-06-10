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
    
 ## Choreographie
  - gleichwertige services
  - services kommunizieren async
  - PRO: Lose Kopplung
  - CON: Async = mehr koordinationsaufwand

## Enterprise Service Bus
  - deployment und versionierung von Services
  - Routen von Nachrichten
  - Standard-Services: Security, Message-Broker, ...
  
## Microservice
The microservice architectural style is an approach to developing a single
application as a suite of small services , each running in its own process and
communicating with lightweight mechanisms , often an HTTP resource API. These
services are built around business capabilities and independently deployable by
fully automated deployment machinery
  - modularized
  - fulfills only ONE task
  - can work together
  - a universal interface should be used
  
## Size of a Microservice
As small as necessary to fit a 5-7 People Team 2 Weeks effort

## Monolith
  - Hat Module
  - Hat Schichten für technologische Aspekte
    - Präsentationsschicht
    - Geschäftslogik
    - Persistenzschicht
  - Komponenten kommunizieren über Methodenaufrufe
  - verwendet eine (relationale) Datenbank
  - CONS:
    - Skalieren (Anwendung MUSS zustandslos sein) => Gesamter Monolith muss kopiert werden
    - DB als Bottleneck => vernichtet evtl. den Skalierungseffekt
    - Änderungen in einem Modul haben auswirkungen auf andere Module
    - neue Entwickler haben es schwer alles zu verstehen
    - Zusammenarbeit zwischen Teams ist sehr aufwendig
    - Anwendung muss als Ganzes deployt werden
    - Selten aktualisiert weil aufwendig zu kontrollieren => Qualitätssicherung
    - Technologieabhängig => z.B. alles in Java geschrieben
    
## Microservice
  - Eigenschaften:
    - Geschäftsprozess Orientierung
    - Modularisierung durch Services
    - Skalierbarkeit auf Service Ebene
    - Dezentrale Datenverwaltung
    - Eventual Consistency
    - Automatisierung des Entwicklungsprozesses
    - Evolutionäre Entwicklung
    - Leichtgewichtige Kommunikation mittels REST oder MOM
    - Ausfallssicherheit
    
## Geschäftsprozess-Orientierung
  - Monolith
    - unterteilung von Entwicklern in Gruppen => Backend, UI, DB, Testing, etc.
  - Microservice
    - Ein Team macht alles und kann auch mehrere Services betreuen
  
## Komponenten/Module
  - sind austauschbar
  - sind wiederverwendbar
  - sind aktualisierbar

## Microservices
  - PROS:
    - Explizite Servicegrenzen
    - Services können unabhängig voneinander deployt werden
    - Fehlerisolierung
    - Bessere Skalierbarkeit
    - verschiedene Datenbanken bei vertschiedneen Services => Key/Value Store, Relational, ...
  - CONS:
    - Aufrufoverhead
    - Schwierigere Fehlerbehandlung
    - Refactoring über Servicegrenzen hinweg ist aufwändig
    
## Kopplung unf Kohäsion
  - Single Responsibility Principle
  - Lose Kopplung: Implementierungsdetails eines Service beeinflussen andere Services nicht
  - Hohe Kohäsion: Zusammengehörende Funktionalität sollte in einem Service gebündelt werden
  
## CAP Theorem (2 of 3 are true)
  - Consistency (Alle Replikate haben den selben Zustand)
  - Avaialbility (Anfragen werden in akzeptabler Zeit abgearbeitet)
  - Partition Tolerance (Ausfallsicherhiet, verlust von Nahcrichten)
    - Microservice ist meist ein AP-System
    
## API-Gateway


## Circuit Breaker
 Erkennt Fehlersituationen und handelt diese
  - offen
  - halb offen
  - geschlossen
  
  
## Spring Cloud
  - zentraler Config Server
  - Eureka
  - Ribbon: Client side Load-Balancing
    - Discovery
    - Feign
