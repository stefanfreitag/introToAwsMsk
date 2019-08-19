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
  * Client &hArr; Broker
  * Broker &hArr; Broker
  * Broker &hArr; Zookeeper
* Monitoring
  * Prometheus
  * Grafana


#### Done

<img src="https://media.giphy.com/media/SxRtWCV8yOYGk/giphy.gif"/>

It just takes a few days.



### MSK-managed approach


#### Why

* Kafka clusters are challenging to setup, scale, and manage
  * Replacements, maintenance, and upgrades
  * HA setup
  * Monitoring and alarming
  * Durable datastore

_Less time managing infrastructure, more time creating value._


#### How

* Manual approach
* Login to AWS Console


##### Create the VPC

* Select _VPC_
* Select _Launch VPC Wizard_
* Select _VPC with a Single Public Subnet_
* Set VPC Name to _AWSKafkaTutorialVPC_
* Set availability zone to _eu-west-1a_
* Set subnet name to _AWSKafkaTutorialSubnet-1_


##### Preps for High Availability

* Select created VPC
* Select _Create Subnet_ 
* Set name tag to _AWSKafkaTutorialSubnet-2_
* Set VPC ID
* Set availability zone to _eu-west-1b_
* Set IPv4 CIDR block to _10.0.1.0/24_


Routing

* Select the created subnet
* Select _Edit route table association_
* Set route id from first subnet

* Repeat steps for 3rd subnet


##### Cluster Time

* Select _Amazon MSK_
* Select _Create Cluster_

* Enter cluster name _MskDemoCluster_
* Select VPC
* Select Apache Kafka Version _1.1.1_
* Fill out information on AZs and subnets
* Set number of brokers to _1_
* Encryption: _Only plaintext traffic allowed_


### Using AWS CDK

* Open VS Code



### Wrap Up - What changes for MSK

* Only get Kafka and Zookeeper endpoints
* Default Kafka configuration can be tweaked
* Monitoring via CloudWatch
* Deployment of jar files not possible



## Further information

* [AWS CDK](https://github.com/aws/aws-cdk)
* [AWS MSK](https://aws.amazon.com/msk/)
* [Kafka](https://kafka.apache.org/)
* [Zookeeper](https://zookeeper.apache.org/)
