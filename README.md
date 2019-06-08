# EJB

## Was ist EJB?

### Welche Komponenten gibt es bei JavaEE/EJB? (nenne mindestens 5)

### Erklären Sie die 5 Arten von Beans bei EJB
  - Session Bean
    - Stateless
    - Stateful
    - Singleton
  - Entity
  - Message Driven
  
 ## Erklären Sie den Unterschied zwischen Abhängigkeitsinjektion und Abhängigkeitsuche
  - Abhängigkeitsuche - InitialContext.lookup (EJB-2.x-Stil)  
  - Abhängigkeitinjektion - @Resource (EJB-3.x)
  
 ### Welche Nachteile hat die Abhängigkeitsuche?
BEACHTE: Die Entkopplung der Komponenten gibt es sowohl bei Abhängigkeitsuche als
auch Abhängigkeitsinjektion.
 ## Zeigen Sie anhand von Code wie ein Session-Bean mit Data-Source-Injektion implementiert werden kann
 
 # MOM
 
 ## Was ist Message Oriented Middleware (MOM)
 
 ### Welche Vorteile bieten MOMs
  - async
  - large scale
  - work modes, z.B. Topics, ...
  - Broker -> Grantierte Zustellung VS push messages
  - Load-Balancing
  - Lose Kopplung von Komponenten
  - Sprach und Platform unabhängig
  - ...
  
### Was ist der Unterschied zwischen MOM und asynchronen Methodenaufrufen?

### WCF-Endpoint-Konfiguration genau erklären (mindestens 4 Parameter) ??? KA
  - address
  - binding
  - binding config
  - contract

### Was ist eine Server Transaction?

### Was ist eine Client Transaction?


### Beispielcode gegeben, bei dem ein Service sich den SessionContext injizieren lässt und am Anfang einer Operations-Implementierung TransactionBegin/? und am Ende TransactionCommit/? aufruft

#### eine Frage in etwa: Warum sollte man es nicht so machen? Wie macht man es richtig? Unter welchen Umständen kann man es aber nicht &quot;richtig&quot; machen/muss es in etwa so machen, wie im Code-Beispiel gezeigt?
Warum sollte man es nicht so machen?
- mehr Technologie-Code (nicht von Geschäftlogik getrennt)
- Transaktions-Code, der immer richtig funktioniert, sehr umständlich bzw. fehleranfällig
(Rollback, Exception-Handling, ... fehlt ja noch im Code-Beispiel)
Wie macht man es richtig?
- Steuerung über Meta-Daten  

Unter welchen Umständen kann man es aber nicht &quot;richtig&quot; machen/muss es in etwa so
machen, wie im Code-Beispiel gezeigt?  

- Annahme: wenn man &gt;innerhalb einer&lt; Service-Operation mehrere Transaktionen benötigt
(reminder, der keine Antwort für diese Frage ist: meistens braucht man eher, dass &gt;mehrere&lt;
Service-Operation in einer Transaktion durchgeführt werden)


### Unter welchen Umständen besser auf Basis WCF umsetzen?


### Unter welchen Umständen besser auf Basis ASP.NET...-API umsetzen?
 
### Wie löst man die Unterstützung verschiedener Formate richtig?

Service verwenden muss.)
```java
  [WebGet(UriTemplate=&quot;.../GetDataXml&quot;, ..., ResponseFormat...=Xml)]
  CompositeType GetDataXml(...);
  [WebGet(UriTemplate=&quot;.../GetDataJson&quot;, ..., ResponseFormat...=Json)]
  CompositeType GetDataJson(...);
```
### Wie kann man es so lösen, dass es den Prinzipien von RESTful entspricht. (Annahme: Frage bezieht sich nicht direkt auf das Server-interne-Interface, sondern auf das, wie der Client das Service verwenden muss.)
- Hauptproblem aus dieser Sicht: unterschiedliche Uris für verschiedene Formate (Annahme:
dann funktioniert automatische Content-Negotation, ... nicht (richtig))  

darüber hinaus (eher Implementierungs-Aspekte):  

- Braucht man überhaupt zwei Methoden?
-- Wozu zwei Methoden, wenn der Rückgabetyp bei beiden gleich ist?
