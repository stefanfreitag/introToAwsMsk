<!-- markdownlint-disable MD012 MD014 -->

# Introduction to AWS Managed Streaming for Apache Kafka



## What we will do

Getting a Kafka cluster up'n' running (dry-run)

* Current approach
* Using AWS MSK



### Current/ Non-managed approach


#### Hardware

<img src="images/alexandre-debieve-FO7JIlwjOtU-unsplash.jpg" alt="" height="500px%"/>

Note:

* Request 3 EC2 instances for Kafka
* Request 3 EC2 instances for Zookeeper
* Request additional EC2 instances (Prometheus, Grafana, ...)


#### Firewall

<img src="images/israel-palacio-ImcUkZ72oUs-unsplash.jpg" alt="" height="500px%"/>

Note:

* Kafka broker &hArr; Zookeeper
* Kafka broker &hArr; Kafka broker
* Kafka &hArr; Clients
* Zookeeper &hArr; Clients

* Prometheus &hArr; Zookeeper
* Prometheus &hArr; Kafka


#### Installation and configuration

<img src="images/chris-yates-iqELIpzpARI-unsplash.jpg" alt="" height="500px%"/>

Note:

* Manual or
* Chef cookbooks


#### Any other business

* Security
  * Skip it for now
* Monitoring
  * Prometheus
  * Grafana
  * Chef cookbooks


#### Heppa

<img src="https://media.giphy.com/media/SxRtWCV8yOYGk/giphy.gif"/>



### MSK-managed approach


#### Why managed Kafka

* Kafka clusters are challenging to setup, scale, and manage
  * Replacements, maintenance, and upgrades
  * HA setup
  * Monitoring and alarming
  * Durable datastore

_Less time managing infrastructure, more time creating value._


## Further information

* [Kafka](https://kafka.apache.org/)
* [Zookeeper](https://zookeeper.apache.org/)
* [AWS MSK](https://aws.amazon.com/msk/?)
