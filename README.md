# DevOps-Project-3tier-Application-Deployment-EKS-RabbitMQ-Memcache-MySQL8-Pod-based
![image](https://github.com/user-attachments/assets/c28e4aa6-5fc0-4669-b8c6-843262208a17)

In the Architecture diagram shown above a basic architecture of three-tier application is shown. In this diagram the first layer or tier is Presentation Layer or web tier. The second layer or tier is Application Layer or Business Tier and third layer or tier is Database Layer or Database tier. For web tier Nginx Service, for Application tier Tomcat and for Database tier MySQL and Memcache(for cache purpose) has been used as shown in the Architecture diagram above.

![image](https://github.com/user-attachments/assets/2cf22143-426e-438b-8604-c0181b69eece)

![image](https://github.com/user-attachments/assets/d83838fa-9fd3-4dee-82f6-8b037f6b520d)

Architecture diagram for three-tier Application and three-tier Application deployment is as shown above.

I have used terraform script as provided in this repository to create the EC2 Instances, ALB, EKS and PostgreSQL RDS.

I have created RabbitMQ cluster with three kubernetes pods. Follow below procedures to achieve the same.

Create Jenkins pipeline for deployment of JBoss Wildfly Application Pods, RabbitMQ Pods, Memcached Pods and MySQL Pods using the Jenkinsfile prresent with this repository.

```
Add a user and permission to the user in RabbitMQ. Assign Role for High Availability (HA) using the commands as shown below.

rabbitmqctl add_user test test
rabbitmqctl set_user_tags test administrator
rabbitmqctl set_permissions -p / test ".*" ".*" ".*"
rabbitmqctl set_policy ha-all ".*" '{"ha-mode":"all","ha-sync-mode":"automatic"}' 
```
![image](https://github.com/user-attachments/assets/e0207b65-dcee-44e1-bb94-9c807d8059e5)

Create Ingress rule using the rabbitmq-ingress-rule.yaml file as present in this repository and do the entry in Route53 hosted-zone and create record set.

