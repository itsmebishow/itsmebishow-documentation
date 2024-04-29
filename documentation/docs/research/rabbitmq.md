# RabbitMQ

## Introduction

What is RabbitMQ?

“RabbitMQ is a message broker: it accepts and forwards messages. You can think about it as a post office: when you put the mail that you want posting in a post box, you can be sure that the letter carrier will eventually deliver the mail to your recipient. In this analogy, RabbitMQ is a post box, a post office, and a letter carrier.” (1)

It has developed by Erlang open source langua

![distributed messaging system](https://miro.medium.com/v2/resize:fit:640/format:webp/1*5x1u9LnHWDiw2ICm9ezTMw.png)

Why we need to use RabbitMQ?

Now that you know what RabbitMQ is, the next question is: why should you use a queue instead of directly sending data from one microservice to the other one. There are a couple of reasons why using a queue instead of directly sending data is better (2)

- Higher availability and better error handling
- Better scalability
- Share data with whoever wants/needs it
- Better user experience due to asynchronous processing

As for usage areas, it will make our job much easier to perform tasks that do not need to be synchronized, such as sending mail, basket operations after adding an order on our e-commerce page, and export (excel, csv) data. (Generally “Message brokers”).

![rabbitmq-workflow](https://www.cloudamqp.com/img/blog/workflow-rabbitmq.png)

The main parts of the rabbitmq:

- A `producer` is a user application that sends messages.
- A `queue` is a buffer that stores messages.
- A `consumer` is a user application that receives message

## Setup

```
// Installation
$ choco install rabbitmq

// install without any
$ choco install rabbitmq --yes

// rabbitmqctl — tool for managing RabbitMQ nodes
# rabbitmqctl status
```

```
// Windows – RabbitMQ has Nodedown Error (Solved)

1. Run RabbitMQ sbin command prompt as administrator.
2. Run "rabbitmq-service remove"
3. Run "rabbitmq-service install"
```

### RabbitMQ Enable Web Management Plugin

To enable a rabbitmq web management plugin on windows, we need to start `RabbitMQ` Command Prompt with administrator privilege, enter the command “`rabbitmq-plugins enable rabbitmq_management`” and execute it.

```
$ rabbitmq-plugins enable rabbitmq_management

// open a url
http://localhost:15672


// To access rabbitmq web management dashboard, the default Username and password of  is “guest” (Username: “guest” | Password: “guest”).
Username: guest
Password: guest
```

---

#### Reference

- [rabbitmq install using choco](https://community.chocolatey.org/packages/rabbitmq)
- [RabbitMQ Installation on Windows](https://www.tutlane.com/tutorial/rabbitmq/rabbitmq-installation)
- [RabbitMQ - Installation: Tutorial](https://www.tutorialspoint.com/rabbitmq/rabbitmq_installation.htm)
- [Rabbit MQ - Publish/Subscribe](https://www.rabbitmq.com/tutorials/tutorial-three-dotnet.html)
- [RabbitMQ Producer and Consumer Solution with Docker in .net Core](https://medium.com/innoviletechrabbitmq-producer-and-consumer-solution-with-docker-in-net-core-9a825d3c2448)
- [Part 1: RabbitMQ for beginners - What is RabbitMQ?](https://www.cloudamqp.com/blog/part1-rabbitmq-for-beginners-what-is-rabbitmq.html)
- [rabbitmqctl - guide](https://www.rabbitmq.com/man/rabbitmqctl.8.html)
- [How to Use RabbitMQ in ASP.NET Core](https://code-maze.com/aspnetcore-rabbitmq/)
- [How do I verify my version of RabbitMQ?](https://www.cloudamqp.com/blog/how-do-i-verify-my-version-of-rabbitmq.html)

#### Solved

- [Unable to perform an operation on node rabbitmq](https://itecnote.com/tecnote/unable-to-perform-an-operation-on-node-rabbitmq/)
