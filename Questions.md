# Java wird mit JSRs standardisiert gehen Sie darauf ein
  - JCP - Java Community Process
  - JavaEE besteht aus einer Reihe von standardisierten APIs
  - JSR
    - Java Specification Request 
    - Dokument welches den Standard beschreibt
    - Referenz Impl
  - TCK
    - Technology Compatibility Kit
    - Test-Suit für Standardkonformität einer Implementierung
  
# Was ist JavaEE und Welche Anforderungen werden an JavaEE gestellt und welche Technologien helfen Entwicklern bei der Umsetzung?
Spezifikation einer Softwarearchitektur zur Entwicklung von Anwendungen mit folgenden
Eigenschaften:
  - Verteilte Komponenten
    - CDI, Interceptors
    - EJB
  - Sicherheitsaspekte sind wichtig
    - Bean Validation
    - Concurency Utils
    - Security
  - Komplexe heterogene Datenkomponenten, Transaktionen
    - JPA
    - JTA
    - JDBC
  - Skalierbarkeit
  - mehrschichtige Architekturen
  - WEB
    - Servlets
    - JSP
    - JSF
  - Messageing
    - JMS
    - JCA
  
# Was ist ein Microprofile?
  - Technologien/APIs
    - JAX RS
    - CDI
    - JSON P
    - JSON B
  - Ziele
    - Standardisierung von Technologien, die für die Implementierung von Microservices notwendig sind.
    - Kürzer Iterationszyklen im Standardisierungsprozess (7 Versionen seit 2017).
    - Entwicklung leichtgewichtiger Laufzeitumgebungen für Microservices.
    
# Was ist der Applikation Server?
  Eine Laufzeitumgebung für JavaEE Anwendungen.
  - Web-Container
    - HTTP
  - EJB-Container
    - RMI
    - IIOP
  - CDI-Container (Bean Management)
  - Transcations/DB
    - JDBC
    - JPA
    - JTA
    - JMS
  - Aufgaben
    - Verwaltung von Komponenten
    - Transaktionen
    - Security
    - Persistenz
    - Namensdienste
    - Asynchrone Nachrichtenverarbeitung
    - Resourcenverwaltung
    - ...
    
# Was sind CDI Beans?
Funktionalität ist Untermenge von EJB
- verwaltet vom Bean Manger
  - Verwaltent Lebwnszyklus
  - Dependency Injection
  - Versenden von Events
  - Interception
  - Bean discovery mode
  
 
# Zustandsloses VS Zustandsbehaftetes Session Bean
  - Stateless Session Beans :
    - Zwischen Client und Bean existiert keine fixe Bindung.
    - Zwischen zwei Methodenaufrufen wird serverseitig kein Zustand gespeichert.
    - Vorteil: Bean kann zwischen verschiedenen Clients „geteilt“ werden (Pooling).
```Java
  // REMOTE
  @Remote public interface PersonnelAdminRemote { … }
  
  @Stateless(name="PersonnelAdminEJB")
  public class PersonnelAdminBean implements PersonnelAdminRemote { … }
  
  // LOCAL
  @Local public interface PersonnelAdminLocal { … }

  @Stateless 
  @Remote(PersonnelAdminRemote.class )
  public class PersonnelAdminBean implements PersonnelAdminRemote, 
  PersonnelAdminLocal { … }
  
  // Höhere EJB Version : keine Interfaces notwendig
  @Stateless
  public class PersonnelAdminBean implements PersonellAdmin { … }
  
  public class WorkLogBean
    @EJB
    private PersonnelAdmin personellAdmin
    @EJB
    private PersonnelAdminBean personellAdminBean; // no interface view
}
```
  - Stateful Session Beans:
    - Während einer Sitzung ist der Client an eine Instanz eines Session Beans gebunden.
    - Häufig benötigte clientbezogene Daten können serverseitig gespeichert werden.
    - Nachteil: erhöhter Ressourcenbedarf.
    
 ```Java
  @Stateful
  public class EmployeeAdminBean implements EmployeeAdminRemote {
    @PersistenceContext private EntityManager em;
    private Employee empl;
    
    public void setEmployee (Long emplId) {
      empl = em.find Employee.class , emplId
    }
    
    public void addLogbookEntry LogbookEntry entry) {
      empl = em.merge(empl);
      empl.addLogbookEntry(entry);
    }
    
    @Remove
    public void close() { }
  }
 ```

# Entity
```Java
@Entity
public class Employee implements Serializable {...}

@Remote
public interface PersonnelAdminRemote {
  Employee findEmployeeById (Long id);
  Collection<Employee> findAllEmployees();
  Long saveOrUpdateEmployee(Employee empl);
}
```

## ASYNC
```Java
  @Local public interface PersonnelAdminLocal {
    @Asynchronous
    public Future<Employee> findEmployeeById (Long id);
}


  @Stateless
  public class PersonnelAdminBean implements PersonnelAdminLocal {
    public Future<Employee> findEmployeeById (Long id) {
      Employee empl = return new AsyncResult<Employee>(empl);
    }
  }
```
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
