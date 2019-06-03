# Project Restful Dogs

A student that completes this project shows that they can:
* troubleshoot running services using both system and programmatically generated logs
* use RabbitMQ to send and receive messages on a message queue

# Introduction

We worked with dogs in plain Java. This project returns dog data using Rest APIs with appropriate logging and makes use of message queues.

# Instructions

Starting with either the dogs-initial application or as a Stretch goals your dogs from yesterday

Add appropriate logging routines. Required logging include
  * Activating actuator endpoints
  * Tomcat logging routed to a separate log file
  * Custom logging under each Get endpoint saying the endpoint has been accessed
    * should only go to console
    * for example when a clients calls /dogs log should say "/dogs accessed"
    * include in log any appropriate parameters sent to the end point
    * for each log, add a date and time stamp.
  * Note: put the log files under the directory /tmp/var/logs/lambdajx You may have to create some directories for this to work.

Create RabbitMQ messaging system with two queues
  * One for each time the /dogs endpoints are accessed
  * One for each time the /dogs/breeds/{breed} endpoint is accessed
  * Each message will contain the endpoint accessed, any parameters used, and the date and time of access. So, very similar to the information in the log. Note: this means a change to the MessageDetail Class - some like:  
    ```import java.io.Serializable;
    
    public class MessageDetail implements Serializable
    {
        private String text;
    ...
    }

Note that RabbitMQ does not like the Java date and time formats. So to add Date and time of access to the RabbitMQ I am suggesting that your message text be something like "message text" + new Date(); That will give an acceptable date and time stamp at the end of your message.

Create a separate application that reads messages from each queue, making sure to add to the message which queue it is from before displaying to the screen.

Stretch Goal
  * Create an application that reads messages from each queue and writes the message to a log file for that queue. So all messages about accessing /dogs would be logged to a file about accessing dogs, all messages about accessing dogs/breeds would be logged to a file about accessing dogs/breeds. The log messages should still go to the console as well.
  * Create a message queue to receive a message each time a dog is created
