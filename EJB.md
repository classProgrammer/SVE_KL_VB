# EJB
## Was ist EJB?
Eine Spezifikation einer Softwarearchitektur zur Entwicklung von Anwendungen mit
folgenden Anforderungen:
 - Komponenten sind verteilt,
 - Sicherheitsaspekte müssen berücksichtigt werden,
 - komplexe heterogene Datenbestände, transaktionale Verarbeitung, 
 - mehrschichtige Architektur,
 - Skalierbarkeit: Unterstützung vieler Clients.
 
## Kürzel
  - JCP ... Java Community Process => Standardisierung
  - JSR ... Java Specification Request
  - TCK ... Technology Compatibility Kit: Test-Suite der Standardkonformität überprüft
  
## Komponenten von JavaEE:
  - CDI
  - Interceptors
  - EJB
  
 ## CDI - Contexts and Dependency Injection
 
 
 ## Aufgaben des Bean-Managers
 - Verwaltung des Lebenszyklus (Erzeugung, Freigabe von Beans, Aufruf von Lebenszyklus Methoden)
 - Abhängigkeitsinjektion
 - Versenden von Events
 - Interception
 
 ## Was ist ein CDI-Bean?
 jede Klasse mit Standardkonstruktor
 
 ## Was ist Bean Discovery?
 Beans werden automatisch gesucht. bean-discovery-mode = "all | annotated | none", annotated ist default.
 
 
## Wo kann Injected werden?
Datenkomponente, Konstruktor, Setter-Method
```Java
public class UserAdminImpl
  @Inject
  private
  UserDao userDao
  
  @Inject
  public
  UserAdminImpl UserDao userDao ) { … }
  
  @Inject
  public
  void setUserDao UserDao userDao ) { … }
}
```
 
## Wozu dient ein Qualifier und wie wird er Verwendet?
Zum auflösen von Mehrdeutigkeit

```Java
@Target({FIELD, TYPE, METHOD, PARAMETER })
@Retention(RUNTIME
@Documented
@Qualifier
public @interface Dao {
  Technology technology () default Technology.JDBC;
}

@Dao(technology Technology.JPA)
public class UserDaoJpa implements UserDao { … }

@Dao(technology Technology.JDBC)
public class UserDaoJdbc implements UserDao { … }

public class UserAdminImpl implements UserAdmin
  @Inject Dao(technology Technology.JPA)
  private UserDao userDao
}
```

## Wozu dienen Interceptoren und wie funktionieren sie?
Trennung von Business-Code und cross-cutting-concerns.  
Anstatt der Zielklasse wird ein Proxy injeziert. Die Methoden des Proxies umschließen die Methoden der Ziel Klasse => Around-Advice
```Java
@Loggable
@Interceptor
public class LoggingInterceptor
  @Inject
  private Logger logger
  
  @AroundInvoke
  private Object intercept InvocationContext ic ) throws Exception {
    logger.info("("----> {} ", ic.getMethod.getName);
    try
      return ic.proceed();
    }
    finally
      logger.info("("<---- {} ", ic.getMethod.getName);
    }
  }
}
```
## Scopes und Kontexte
Ein Bean lebt in einem Kontext. Es wird automatisch erzeugt wenn es im Kontext das erst mal angesprochen wird und es wird zerstört wenn der Kontext beendet wird. Beans im selben Kontext teilen sich den Zustand.  

Der Scope bestimmt die Lebensdauer eines Beans und legt fest welch Instanz bei der Abhängigkeitsinjektion zugeteilt werden.  
Scopes: 
 - RequestScoped : Bean wird dem Request Kontext zugeordnet.
 - SessionScoped : Bean wird einer HTTP Session zugeordnet.
 - ConversationScoped : Beginn und Endes des Kontexts kann explizit festgelegt
 - ApplicationScoped : Zuordnung zu Kontext, der während der gesamten Laufzeit der Anwendung existiert.
 
## Was ist ein Stereotype?
  Sammlung von Annotationen die eine Rolle ausdrücken z.B. Controller, Service
  
## Wozu dient ein Session-Bean?
  Durchführung von Geschäftslogik, beschreiben von Abläufen,  
  
  Arten:
  - Stateless Session-Beans
  - Stateful Session-Beans
  - Singeltons
 
 Entity-Bean => Modellierung von Zuständen und Daten => oft verwendet als Parameter von Geschäftslogik-Methoden
 
## Stateless VS Stateful
 - Stateless Session Beans :
   - Zwischen Client und Bean existiert keine fixe Bindung.
   - Zwischen zwei Methodenaufrufen wird serverseitig kein Zustand gespeichert.
   - Vorteil: Bean kann zwischen verschiedenen Clients „geteilt“ werden (Pooling).
- Stateful Session Beans:
   - Während einer Sitzung ist der Client an eine Instanz eines Session Beans gebunden.
   - Häufig benötigte clientbezogene Daten können serverseitig gespeichert werden.
   - Nachteil: erhöhter Ressourcenbedarf.
