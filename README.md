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
  * Note: put the log files under the directory /var/logs/lambdajx Feel free to create and necessary subdirectories.

Create RabbitMQ messaging system with two queues
  * One for each time the /dogs endpoints are accessed
  * One for each time the /dogs/breeds/{breed} endpoint is accessed
  
Create a separate application that reads messages from each queue, making sure to add to the message which queue it is from before displaying to the screen.

Stretch Goal
  * Create an application that reads messages from each queue and writes the message to a log file for that queue. So all messages about accessing /dogs would be logged to a file about accessing dogs, all messages about accessing dogs/breeds would be logged to a file about accessing dogs/breeds. The log messages should still go to the console as well.
  * Create a message queue to receive a message each time a dog is created
