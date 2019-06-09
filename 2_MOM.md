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

##
