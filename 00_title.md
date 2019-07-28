<!-- markdownlint-disable MD012 MD014 -->

# Managing Kafka



## What is Kafka

> * Open-source stream-processing software platform
> * Aims to provide a unified, high-throughput, low-latency platform for handling real-time data feeds
> * Massively scalable pub/sub message queue designed as a distributed transaction log

[Source](https://en.wikipedia.org/wiki/Apache_Kafka)



## Exisiting installations

|           |  Node 1   | Node 2   | Node 3  
|   ---     |   ---     |   ---    |  ---
| Zookeeper | ln000111  | ln000112 | ln000113
|  Kafka    | ln000114  | ln000115 | ln000116

Production environment (All sub-teams)


|             |  Node 1   | Node 2   | Node 3  
|---          |   ---     |   ---    | ---
| Zookeeper   | ln000106  | ln000107 | ln000108
|  Kafka      | ln000103  | ln000104 | ln000105

Staging environment (All sub-teams)


|           |  Node 1
|  ---      |  --- |
| Zookeeper |  lb001460 |
|  Kafka    |  lbeu0010 |

UAT (Java)


### Side note

... and more in other teams

* Endur SOLID
* Production and Development environment in CPD


## How ours were setup

* Chef cookbooks for all environments
* Separate cookbooks for
  * Kafka cluster/ Zookeeper cluster
  * Single node Kafka/ Single node Zookeeper


### Applied changes

* Kafka Manager  
  * Disable start of service at boot time
  * Version upgrade
* Kafka  
  * Configuration settings
    * Data retention
    * Security (UAT)


* Other bits 'n' bites I am not aware of
* Changes may be reflected in Chef cookbooks


... or not.


* Imho no one knows
  * the exact configuration of the services
  * what happens when the cookbooks are re-run


![Alt Text](https://media.giphy.com/media/wuc6lU7kbu6wE/giphy.gif)


## Immutable Infrastructure

> [...] infrastructure paradigm in which servers are never modified after they're deployed. If something needs to be updated, fixed, or modified in any way, new servers built from a common image with the appropriate changes are provisioned to replace the old ones. After they're validated, they're put into use and the old ones are decommissioned.

[Source](https://www.digitalocean.com/community/tutorials/what-is-immutable-infrastructure)


### In Short

![Alt Text](https://media.giphy.com/media/KBE8Xk9qeZVWhPz5MX/giphy.gif)



## Chef


### What can be managed

* OS-related settings
  * software packages
  * logrotate, cron

* Basic configuration
  * Kafka, Kafka Manager, JMX Exporter
* Security related configuration
  * Kafka


### Recommended way

Setup a local dev environment

* Install
  * Chef Development Kit or Workstation
* Checkout cookbook repository
* Apply change to cookbook/ recipes
* Test changes
* Increment version in metadata.rb
* Commit, push and create pull request


### For the are brave

![Alt Text](https://media.giphy.com/media/xUA7b9BGCRbVlYnnLq/giphy.gif)

* Apply change to cookbook/ recipes
* Increment version in metadata.rb
* Commit and push



# Demo Time

* Cookbook file
* Template
* User and ACL


# Backup slides


## Assigning cookbooks

* Cloud Eco Hub
  * Manage run list
* knife
  * comes with Chef DK/ Workstation
  * requires personalized certificate


## Applying cookbooks


* Cloud Eco Hub
  * Initiate Chef client
* Login to host and trigger chef-client manually
* cron job



## Further information

* [Chef](https://www.chef.io/)
* [Chef Development Kit](https://downloads.chef.io/chefdk)
* [Chef Workstation](https://downloads.chef.io/chef-workstation/stable)
* [Kafka](https://kafka.apache.org/)
* [Kafka cookbook for clustered setup](http://stash.rwe.com/projects/CHEF/repos/rwest_caogasce_kafka/browse)
* [Kafka cookbook for single instance setup](http://stash.rwe.com/projects/CHEF/repos/rwest_caogasce_kafka_single/browse)
* [Zookeeper](https://zookeeper.apache.org/)
* [Zookeeper](http://stash.rwe.com/projects/CHEF/repos/rwest_caogasce_zookeeper_single/browse)
* [Kafka Manager](https://github.com/yahoo/kafka-manager)
