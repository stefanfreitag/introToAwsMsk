<!-- markdownlint-disable MD012 MD014 -->

# Introduction to AWS Managed Streaming for Apache Kafka



## What we will do

Getting a Kafka cluster up'n' running

* Manual approach
* Using AWS MSK



### Manual approach


#### Hardware

<img src="images/alexandre-debieve-FO7JIlwjOtU-unsplash.jpg" alt="" height="500px%"/>

Note:

* Request 3 EC2 instances for Apache Kafka
* Request 3 EC2 instances for Apache Zookeeper
* Request additional EC2 instances for hosting e. g.Prometheus and Grafana


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

* Manual
* Automated (Ansible, Chef, Puppet, ...)


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


Downside

_It just takes a few days._



### Managed solution - AWS MSK


#### Why

* Kafka clusters are challenging to setup, scale, and manage
  * Replacements, maintenance, and upgrades
  * HA setup
  * Monitoring and alarming
  * Durable datastore

_Less time managing infrastructure, more time creating value._


#### How

* Login to AWS Console


##### VPC

<img src="./images/thomas-jensen-qTEj-KMMq_Q-unsplash.jpg" alt="" height="500px%"/>

Note:

* Select _VPC_
* Select _Launch VPC Wizard_
* Select _VPC with a Single Public Subnet_
* Set VPC Name to _AWSKafkaTutorialVPC_
* Set availability zone to _eu-west-1a_
* Set subnet name to _AWSKafkaTutorialSubnet-1_


##### High Availability

Note:

* Select created VPC
* Select _Create Subnet_ 
* Set name tag to _AWSKafkaTutorialSubnet-2_
* Set VPC ID
* Set availability zone to _eu-west-1b_
* Set IPv4 CIDR block to _10.0.1.0/24_


Routing

Note:

* Select the created subnet
* Select _Edit route table association_
* Set route id from first subnet

* Repeat steps for 3rd subnet


##### Cluster Time

<img src="./images/kent-pilcher-jW8hkB_Qmj8-unsplash.jpg" alt="" height="500px%"/>

Note:

* Select _Amazon MSK_
* Select _Create Cluster_

* Enter cluster name _MskDemoCluster_
* Select VPC
* Select Apache Kafka Version _1.1.1_
* Fill out information on AZs and subnets
* Set number of brokers to _1_
* Encryption: _Only plaintext traffic allowed_


### Using AWS CDK

* [Github](https://github.com/stefanfreitag/msk_demo)



### Wrap Up

* Serverless: MSK provides Kafka and Zookeeper endpoints
* Default Kafka configuration can be tweaked
* Monitoring via CloudWatch
* Deployment of jar files not possible


## Further information

* [AWS CDK](https://github.com/aws/aws-cdk)
* [AWS MSK](https://aws.amazon.com/msk/)
* [Kafka](https://kafka.apache.org/)
* [Grafana](https://github.com/grafana/grafana)
* [Prometheus](https://prometheus.io/)
* [Zookeeper](https://zookeeper.apache.org/)
