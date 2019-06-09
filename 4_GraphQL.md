# GraphQL

## Eigenschaften von REST
 - Zustandslosigkeit
 - Ressourcen Zentriertheit
 - Vordefinierte Operationen auf Ressourcen
 - Unterstützung mehrere Repräsentationen der Ressourcen
 
 ## Probleme von REST
 - Unterschiedliche Interpretationen von REST
 - Struktur der Daten ist weitgehend statisch
    - übertragene Daten werden von Clients nur teilweise benötigt.
 - Viele Clients mit unterschiedlichen Anforderungen, die sich häufig ändern
    - REST API wird mit Funktionen überladen
    
 ## Vortiele von GraphQL
  - kein overfetching (mehr Daten bekommen als notwendig => overhead an Daten)
  - kein underfetching (zusätzliche Requests um alle benötigten Daten zu bekommen => overhead an Requests)
      - n+1 Problem => Detaildaten zu Elementen eines Behälters müssen nachgeladen werden (bei REST)
  - Flexibel an Anforderung von Clients anpassbar => REST = viele Endpunkte notwendig
  - Anfragen werden auf der Backend-Seite analysiert => Client definiert die Daten, Resolver handelt Datenzugriff
  
  ## Konzepte von GraphQL
    - SDL ... Schema Definition Language
      - type
      - enum
      - scalar
      - Fields
      - interface
      - inheritance
    - Queries => GET
    - Mutations => POST, UPDATE, DELETE, ...
    - Subscription => auto update
    - Resolver => für komplexe Typen
    
    
  ## Architektur von GraphQL
    - Transportprotokoll nicht vorgegeben => HTTP, TCP normal
    - Anwendung
      - Service-Oriented: GraphQL greift auf Serviceschicht zu
      - Datenzentriert: interagiert direkt mit DB
      - Integrationszenario: GraphQL-Server führt die Daten mehrere Anwendungen zusammen => Client muss nicht mehrere REST calls absetzen
    - Das GraphQL-Service ist über Resolver mit dem Backend verbunden
    
      
    
