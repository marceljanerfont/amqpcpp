amqpcpp
=======
**amqpcpp** is a C++ library for Message Queue Server RabbitMQ (http://www.rabbitmq.com/) and support the AMQP (Advanced Message Queuing Protocol http://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol ). The C++ library is using the C-rabbitmq client library (https://github.com/alanxz/rabbitmq-c).

INSTALL
-------

Download RabbitMQ-C client library from https://github.com/alanxz/rabbitmq-c
git clone git://github.com/alanxz/rabbitmq-c.git

Download RabbitMQ protocol code-generation and machine-readable specification from http://hg.rabbitmq.com/rabbitmq-codegen/
hg clone  http://hg.rabbitmq.com/rabbitmq-codegen/

Compile and install librabbitmq
make install

cd amqpcpp 

edit the Makefile if it is need.
make 

for install copy the libamqpcpp.a to /usr/local/lib or other system library dir.

TODO
----
- Unit test: *gtest*

TODO DOCUMENTATION
------------------
- message broker user-case: workload balance, publisher-subscriber-topic, RPC 
- amqp exchanges, queues and routing keys
- amqp exchange types
- queue declaration and binding
- messages, ttl, ack
- DLX
- ...

