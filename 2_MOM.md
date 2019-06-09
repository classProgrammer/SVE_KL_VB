# MOM - Message Oriented Middleware

## Base Concepts
  - Synchronous (Client blocks and waits for return param)  
    CLIENT ---Input Param---> Server  
    CLIENT <--Return Param--- Server
  - Asynchronous (Client not blocked, message is processed later and process is watched by broker)  
    SENDER---Message-->BROKER---Mesage-->RECEIVER  
    
  ## Advantages of Async Messageprocessing
    - Sender not blocked
    - Sender/Reciever can be partly offline
      - e.g. Maintenance
    - Lose Kopplung - Loose Coupling
      - change of components
      - Sender/Receiver do not need to know anything about each other
      - Language independent => Sender C#, Receiver Java etc.
      - New functionality can be added without effect for existing sender
    - Load Leveling => Queue can store messages when there are more requests than can be processed for a short period of time
    - Load Balancing => scalable, several queues, several producers and consumers
    - Scalable Broker => several Broker instances
    - Availability/Reliability => several instances, load balancing, load leveling, ...
    
  ## Java Message Service JMS
    - publisher-subscriber(Topic): all registered receivers get all messages
    - point-to-point: one receiver gets exactly one message
    - gesicherter Nachrichtrenaustausch über Bestätigungsnachrichten oder verteilten Transaktionen
    - Bestätigungs-Modi: einzeln(automatisch vom Broker), bündelweise, , transaction, einzeln(explizit)
    
  ## JMS-Producer
    - Connection Factory
    - Destination
    - Queue/Topic
    - Connection
    - Session
    - Message Producer = session.createProd(destination)
    - Messages
    
  ## JMS 2.0 (Context = Session + Connection) Producer
    - Connection Factory
    - Destination
    - Try(JMSContext context = factory.createContext())
    - context.createProducer
    - context.createMessage
    - producer.send(destination, message)
  ## JMS 2.0 Consumer Synchronous
    - ConnectionFactory
    - Queue
    - factory.createContext
    - consumer = context.createConsumer(queue)
    - message = consumer.receive()
    - message.acknowledge()
    
  ## JMS 2.0 Consumer Async    
    - ConnectionFactory
    - Queue
    - factory.createContext
    - consumer = context.createConsumer(queue)
    - consumer.setMessageListener(listener)
 ```Java
MessageListener listener = new MessageListener ()
@Override
public void onMessage (Message message)
  // process Message
  message.acknowledge();
}
 ```
 
 ## AMQP ... Advanced Message Queuing Protocol
  - Binärprotokoll auf Anwendungsebene
  - Offener Standard
  - Unabhängig von der Programmiersprache
 - Gibt gewisse Konzepte (Exchange, Queue etc.) vor, definiert aber keine API.
 - RabbitMQ ist referenz Implementierung für AMQP

## AMQP Components
  - Netzwerkprotokoll
  - Verhalten aud Serverseite
  - Exchange: routes messages to queue
  - Queue: FIFO-Datastructure, Stores to RAM or Hard Drive 
  - Binding: Rule for submission to queues (topic queue etc.)
  
## Java Client
  - Connection Factory
  - try(connection = factory.newConection(), channel = connection.createChannel())
  - channel.exchangeDeclare()
  - channel.queueDeclare()
  - channel.queueBind()
  
## Senden von Nachrichten
  - kein Rückmeldung (Fast)
  - bei Fehler
  - Bestätigung
  - alternative exchanges
  - hochverfügbare Queues
  - Transactions
  - hochverfügbare Queue + Transaction
  - Persistieren von Nachrichten auf Festplatte (Reliable)
  
  
## High Availability
  Mirrored Queues
  
## Senden von Nachrichten
  - Bestätigungs Bündel (Fast)
  - Verarbeitung + Bestätigung + Prefetch
  - Verarbeitung + Bestätigung
  - Verarbeitung mit Transaktion
  - Synchron (Reliable)
  
  
## Consumer Prefetch
  - Unbestätigte Nachrichten die ein Consumer halten darf 
  
  
## Eigenschaften von Queues
  - durable: Persistant or Temporary Queue
  - exclusive: Nur ein Consumer
  - autoDelete: Queue wird gelöscht wenn sich der letzte Consumer abmeldet
  - arguments: Ablaufzeit einer Queue, Max-Lifespan von Nachrichten, max Anzahl von Nachrichten/Queue
  
## Exchange Types
  - Fanout: Nachricht -> alle Queues
  - Direct: Nachricht -> alle Queues mit Routing-Key
  - Header: Nachricht -> alle Queues mit den selben Properties(ALL) oder einem Property match (ANY)
  - Topic: Nachricht -> alle Queues mit dem Topic
  
  
## Scaling of RabbitMQ
  - worker queue
  - Consistent Hash Exchange => Hashfunction verteilt arbeit auf Queues
  - Cluster => Mehrere RabbitMQ-Instanzen werden zu einem Cluster zusammengefasst
  
## Behandlung unbestätigter Nachrichten
  - Zurück in die Queue
  - löschen der Nachricht
  - Dead Letter Queue
  
  
## JMS vs. AMQP
 - AMQP
    - Offener Standard (OASIS, ISO) zum Austausch von asynchronen Nachrichten.
    - Viele Implementierungen von verschiedenen Herstellern (Apache Qpid ,
RabbitMQ, SwiftMQ , Azure Service Bus,
    - Client APIs für viele Plattformen (.NET, Java, Node.js, PHP, Python, …)
    - Unterstützung auch durch JMS Broker (z. B. ActiveMQ).  
    
  - Abgrenzung zu JMS
    - JMS definiert API, das verwendete Protokoll ist proprietär.
    - AMQP definiert das Protokoll auf binärer Ebene.  
    
  - Konzeptionelle Unterschiede:
    - Mithilfe von Exchanges können bei AMQP Nachrichten flexibel auf Queues
aufgeteilt werden.
    - RabbitMQ bietet die Möglichkeit, Cluster zu bilden -> bessere Skalierbarkeit.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
