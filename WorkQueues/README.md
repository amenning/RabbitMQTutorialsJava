# Work Queues RabbitMQ Example
(https://www.rabbitmq.com/tutorials/tutorial-two-java.html)

Distributing tasks among workers (the competing consumers pattern)

This contains two programs in Java from this tutorial; a new-task that sends a single message from the command line, and a worker that receives messages and performs a task.  In this case, for every '.' in the sent message, the worker will pause for 1 second.  

Some aspects to note this example uses:
* Manual message acknowledgment - ensures messages aren't lost if a worker dies while processing a message.  
* Durable queues and messages - ensures queues and messages aren't lost if RabbitMQ crashes or is turned off
* Fair dispatch - ensures that each worker doesn't receive a new message until it has processed and acknowledged the previous message 

In order to run this example do the following:

```
# Make sure you have rabbitmq running.  For example, on a mac with rabbitmq installed through brew, run the following
brew services start rabbitmq

# Build the maven package.  This will create two executables - receiver-runnable.jar and send-runnable.jar
mvn clean verify compile package

# In one or more separate terminals, start the worker runnable
java -jar target/worker-runnable.jar

# You will see the following
 [*] Waiting for messages. To exit press CTRL+C

# In one or more separate terminals, send a message by running the send runnable
java -jar target/new-task-runnable.jar Test......

# In the terminal with the new task runnable, you will see:
 [x] Sent 'Test......'
 
# In one of the worker terminals with the worker runnable, you will see:
 [x] Received 'Test......'
 [x] Done
```

