# "Hello World!" RabbitMQ Example
(https://www.rabbitmq.com/tutorials/tutorial-one-java.html)

This contains two programs in Java from this tutorial; a producer that sends a single message, and a consumer that receives messages and prints them out.  In order to run this example do the following:

```
# Make sure you have rabbitmq running.  For example, on a mac with rabbitmq installed through brew, run the following
brew services start rabbitmq

# Build the maven package.  This will create two executables - receiver-runnable.jar and send-runnable.jar
mvn clean verify compile package

# In one terminal, start the receiver runnable
java -jar target/receiver-runnable.jar

# You will see the following
 [*] Waiting for messages. To exit press CTRL+C

# In a separate terminal, send a message by running the send runnable
java -jar target/send-runnable.jar

# In the terminal with the send runnable, you will see:
 [x] Sent 'Hello World!'
 
# In the terminal with the receiver runnable, you will see:
 [x] Received 'Hello World!'
```

