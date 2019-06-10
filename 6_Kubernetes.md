# Kubernetes
- Kubernetes ist eine Plattform zum Betrieb von Service orientierten Anwendung.
- Services werden in Form von Containern deployt.
- Kubernetes unterstützt viele Anforderungen an Microservice Architekturen
  - Skalierbarkeit
  - Automatisches Deployment
  - Fehlerresistenz
  
## Anforderungen an Microservice orientierte Anwendungen
  - Unabhängigkeit der Services
  - Skalierbarkeit
  - Continuous Deployment
  - Resilienz (automatisches Erkennen und Ersetzen von Ausfällen)
  
  
## Komponenten
  - Master-Node
  - API-Server: 
    - Zentrale Komponente, die von anderen Komponenten und von Clients angesprochen wird
    - Bietet CRUD Operationen für Kubernetes Objekte in Form einer REST API
    - Führt Authentifizierung, Autorisierung und Validierung durch
    - Event basiert
  - Scheduler
    - Entscheidet darüber, auf welchem Node ein Pod laufen soll (via API
  - Controller Manager
    - Koordiniert Controller für Kubernetes Objekte: Nodes, Services, ReplicaSets ,Deployments, Services, …
  - kublet
    - Ist für alle Prozesse am Worker Node verantwortlich:
  - Container Runtime
    - Lädt Images herunter und startet Container.
    - z.B. Docker
  - etcd: 
    - key value store
    - Persistierung von Daten
  - Service Proxy ( kube proxy)
    - Sorgt dafür, dass Datenpakete, die an Services geschickt werden, an Pods weitergeleitet werden
## Pods
  - Gruppe von Containern
  - Ein Pod mit allen Containern läuft auf einem Knoten
  - Service = Gruppe von Pods mit der sleben Funktion
  - Anzahl an Pods ist flexible => Skalability
  - fixer Kommunikationsendpunkt => ein Service = eine Addresse
  - load balancing => anfragen an Service werden auf pods verteilt
