
# RabbitMQ

# Ports

RabbitMQ [networking](https://www.rabbitmq.com/networking.html) lists:

 * 5672, 5671: used by AMQP 0-9-1 and AMQP 1.0 clients without and with TLS
 * 15672, 15671: HTTP API clients, management UI and rabbitmqadmin, without and with TLS (only if the management plugin is enabled)

# Server
run 

    docker run -d --hostname rabbit --name rabbit -p 8080:15672  -p 5672:5672 -p 5671:5671 -e RABBITMQ_DEFAULT_USER=rabbit -e RABBITMQ_DEFAULT_PASS=rabbit rabbitmq:3-management


# Clients

See notes on [AMQP Transports](https://docs.celeryq.dev/projects/kombu/en/latest/userguide/connections.html)

 * [librabbitmq](https://pypi.org/project/librabbitmq/)
 * [kombu](https://docs.celeryq.dev/projects/kombu/en/latest/index.html)
 * [amqp](https://pypi.org/project/amqp/)