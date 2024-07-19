# DevOps-Project-3tier-Application-Deployment-EKS-RabbitMQ-Memcache-MySQL8-Pod-based
![image](https://github.com/user-attachments/assets/bf16fb2c-b5aa-4f23-97da-603dda586f0c)

In the Architecture diagram shown above a basic architecture of three-tier application is shown. In this diagram the first layer or tier is Presentation Layer or web tier. The second layer or tier is Application Layer or Business Tier and third layer or tier is Database Layer or Database tier. For web tier Nginx Service, for Application tier Tomcat and for Database tier MySQL and Memcache(for cache purpose) has been used as shown in the Architecture diagram above.

![image](https://github.com/user-attachments/assets/e3f97f5d-d298-4c65-a265-1f8347bf75c8)

![image](https://github.com/user-attachments/assets/a4255a52-21b5-4fe7-b855-cb788dd90b69)

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
![image](https://github.com/user-attachments/assets/ff8973de-ab40-498e-8f85-869b618e9679)

Create Ingress rule using the rabbitmq-ingress-rule.yaml file as present in this repository and do the entry in Route53 hosted-zone and create record set.

![image](https://github.com/user-attachments/assets/54efb7ac-f9f6-4cd6-8b78-a2e611dfa8a3)
![image](https://github.com/user-attachments/assets/6f6a1bd8-d11f-48a6-8793-fe369c945f1e)
![image](https://github.com/user-attachments/assets/cc2ce1e6-6e61-45dd-8586-f361be8527a9)

The Source Code is present in GitHub Repository https://github.com/kamalmohan217/Three-tier-WebApplication-Wildfly.git.
![image](https://github.com/user-attachments/assets/0b8c58d3-ddf5-47b9-a914-8cdc2a58558b)
![image](https://github.com/user-attachments/assets/e63f932f-314d-41f5-8c73-a6dc01cd24d2)

Install Plugins **Nexus Artifact Upload, Pipeline Utility Step and SonarQube-Scanner** as shown in screenshot below.
![image](https://github.com/user-attachments/assets/fe3cbeb6-bd01-483d-8807-9c07d466d64e)
![image](https://github.com/user-attachments/assets/0b24207d-ad1b-49b9-9aad-f4344986efa1)

Now Run the Jenkins Job. Create the URL using ingress rule for service present in the file ingress-rule.yaml in this repository. Do the entry in Route53 hosted-zone and create the record set. Access the newly created URL and provide username admin_vp and password admin_vp.

![image](https://github.com/user-attachments/assets/b36ce511-201e-4a43-9a75-794ba3736755)
![image](https://github.com/user-attachments/assets/ccb6422b-f89c-4c84-8f90-5c856ad502f4)
![image](https://github.com/user-attachments/assets/c129f251-f09b-4eaa-9d33-136553c4cdc7)
![image](https://github.com/user-attachments/assets/bc595ebc-6816-472f-afc4-17ddecece21e)

When you click on the User for the first time it will get the values from MySQL Database and store it in Memcache, so that next time when you click on the same user it will provide the values from the Memcache itself.

![image](https://github.com/user-attachments/assets/bb65bba0-4bb9-45ad-b1dc-931d683ad97c)
![image](https://github.com/user-attachments/assets/a57fc4aa-bb3b-4599-a53c-cb53a12f5a10)

After running the Jenkins Pipeline Screenshots for RabbitMQ, SonarQube, Nexus Repository and ArgoCD are as shown in the Screenshot below.
![image](https://github.com/user-attachments/assets/a3d598cd-2527-4010-97cb-bca18c1e05f5)
![image](https://github.com/user-attachments/assets/134a3844-8df3-4c5f-ad06-157b3e5106f0)
![image](https://github.com/user-attachments/assets/d31c154a-2285-48bf-b0cb-8ea7027ea2c8)
![image](https://github.com/user-attachments/assets/8f55a3d5-7b42-4fa8-acf0-4babb6abef58)
![image](https://github.com/user-attachments/assets/7ba7649d-ca41-4cd1-b875-8c89961868bd)
![image](https://github.com/user-attachments/assets/0406b31a-47f7-4b04-8e28-929f3f108f43)


<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
```
Source Code:-  https://github.com/kamalmohan217/Three-tier-WebApplication-Wildfly.git
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
