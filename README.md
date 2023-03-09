# AWS-EC2-PROMETHEUS-GRAFANA-APPLICATION-MONITORING

## Tools and AWS services used:
- AWS EC2
- AWS security group 
- Promethesu 
- Grafana 

## Prerequisite:
Prometheus EC2 instance t2.micro 
Node EC2 instances to monitor
Security Groups Configured properly
Clone this git repo

## Create EC2 instaces

## Login into AWS EC2 isntance :

```
ssh -i <key_file_path> username@IP
```
Security Groups Configured on EC2 Instances
Port 9090 — Prometheus Server

Port 9100 — Prometheus Node Exporter

Port 3000 — Grafana

Prometheus EC2 Instance
Configure the security group on EC2 Instance where Prometheus Server is installed as shown below :



Node EC2 Instances
Configure the security group on EC2 Instance which you want to monitor and where you will install Node Exporter as shown below:

One entry is from your IP and one entry is the IP of the EC2 instance where Prometheus server is installed so that Prometheus server can read the metrics which is exposed on the Node server.


## Prometheus Architecture
Prometheus is an open source tool for monitoring and alerting applications
a multi-dimensional data model with time series data identified by metric name and key/value pairs
Uses PromQL ( Prometheus Query Language)
time series collection happens via a pull model over HTTP
Targets System which you want to monitor can be identified using Service Discovery or by static configuration in the yaml file
Below is the diagram of Prometheus architecture and its components



Prometheus Server: This component is the central component that collects the metrics from multiple nodes. Prometheus uses the concept of scraping, where target systems’ metric endpoints are contacted to fetch data at regular intervals.
Node Exporter: This is called a monitoring agent which we installed on all the target machines so that Prometheus can fetch the data from all the metrics endpoints
Push Gateway: Push Gateway is used for scraping metrics from applications and passing on the data to Prometheus. Push Gateway captures the data and then transforms it into the Prometheus data format before pushing.
Alert Manager: Alert Manager is used to send the various alerts based upon the metrics data collected in Prometheus.
Web UI: The web UI layer of Prometheus provides the end user with an interface to visualize data collected by Prometheus. In this, we will use Grafana to visualize the data.
