# Publish/Subscribe RabbitMQ Example
(https://www.rabbitmq.com/tutorials/tutorial-three-java.html)

Distributing tasks among workers (the competing consumers pattern)

This contains two programs in Java from this tutorial; a emit-log that sends a single message from the command line, and a receive-logs program that receives messages.  This is an example of the publish/subscribe pattern.

In order to run this example do the following:

```
# Make sure you have rabbitmq running.  For example, on a mac with rabbitmq installed through brew, run the following
brew services start rabbitmq

# Build the maven package.  This will create two executables - receive-logs-runnable.jar and emit-log-runnable.jar
mvn clean verify compile package

# In one or more separate terminals, start the receiver runnable
java -jar target/receive-logs-runnable.jar

# You will see the following
 [*] Waiting for messages. To exit press CTRL+C

# In one or more separate terminals, emit a message by running the emit-log runnable
java -jar target/emit-log-runnable.jar Test......

# In the terminal with the emit log runnable, you will see:
 [x] Sent 'Test......'
 
# In all of the receive logs terminals, you will see:
 [x] Received 'Test......'
```

