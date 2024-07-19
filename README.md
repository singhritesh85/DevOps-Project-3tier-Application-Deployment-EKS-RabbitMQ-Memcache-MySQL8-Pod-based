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

![image](https://github.com/user-attachments/assets/d973e300-ef31-4e54-87b8-4cb177d2945e)
![image](https://github.com/user-attachments/assets/e9152da5-c76c-4cd1-a018-43d89a870fa0)
![image](https://github.com/user-attachments/assets/2a63222d-df4b-43ae-b026-07a0e034b27f)

The Source Code is present in GitHub Repository https://github.com/singhritesh85/Three-tier-WebApplication-Wildfly.git.

I have created configmap to import the tables into the database. This step was done in the Jenkins Job itself as shown in the screenshot below.
![image](https://github.com/user-attachments/assets/f2f4c972-3c6f-485d-b66d-32367aea0f7d)
![image](https://github.com/user-attachments/assets/b0a90a18-899e-40dc-b050-ae350db81be9)

Install Plugins **Nexus Artifact Upload, Pipeline Utility Step and SonarQube-Scanner** as shown in screenshot below.
![image](https://github.com/user-attachments/assets/81f07754-81b7-4e0b-b85a-dd9f0eec38c8)
![image](https://github.com/user-attachments/assets/71e02e2d-ebac-4ae1-909d-d6c04902a554)

Now Run the Jenkins Job. Create the URL using ingress rule for service present in the file ingress-rule.yaml in this repository. Do the entry in Route53 hosted-zone and create the record set. Access the newly created URL and provide username admin_vp and password admin_vp.

![image](https://github.com/user-attachments/assets/7f546dd5-5802-4eb2-ab63-77d673eb663a)
![image](https://github.com/user-attachments/assets/a52ed7fa-57e6-4067-80b0-3e0e2cb58f99)
![image](https://github.com/user-attachments/assets/45f1a5e7-f4e5-4e2b-af0d-e30fd9684427)
![image](https://github.com/user-attachments/assets/6549f8dc-ab34-4b39-828f-d6f7cbcd24a2)

When you click on the User for the first time it will get the values from MySQL Database and store it in Memcache, so that next time when you click on the same user it will provide the values from the Memcache itself.

![image](https://github.com/user-attachments/assets/2c18ab72-059b-4173-95be-155e7fa4837c)
![image](https://github.com/user-attachments/assets/1aa916de-2799-4c99-99ec-29d0f5827163)

After running the Jenkins Pipeline Screenshots for RabbitMQ, SonarQube, Nexus Repository and ArgoCD are as shown in the Screenshot below.
![image](https://github.com/user-attachments/assets/937562a6-6207-4133-8a20-2db557c10bfc)
![image](https://github.com/user-attachments/assets/a7191081-b704-46b5-acb4-5e4bc5e31823)
![image](https://github.com/user-attachments/assets/e683ea54-1cbe-4185-b1e0-20ecc263a0d1)
![image](https://github.com/user-attachments/assets/12b99f56-972c-4b65-a8e6-270775d8ea31)
![image](https://github.com/user-attachments/assets/9c74c46f-eafd-4de1-bcc2-85f8d9e5306b)
![image](https://github.com/user-attachments/assets/ff1cb619-4913-4f9a-b29a-42336cf618fd)


<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
```
Source Code:-  https://github.com/singhritesh85/Three-tier-WebApplication-Wildfly.git
```
<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
```
Reference:-  https://github.com/logicopslab/vprofile-project.git
```
