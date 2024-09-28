Auto Scaling is used for automatic scaling up and scaling down.
Load balancer is used to distribute the incoming traffic across multiple targets.

When you launch a business application, you want it to reach as many users as possible, right? 

But how many people your application can serve at one time depends on its server’s technical capacities. 

Let’s understand this concept with an example. Say, your launch an application where you feel the daily user traffic will be around 10,000 visitors. Thus, you invest in a server that can deal with 10,000 visitors with ease. 

But let’s say one of your marketing campaigns performs really well. And more than 15,000 visitors flock to your app at once. That would cause hindrances in user experience as the server would have maxed out on its capacity. In such a situation, you’d require a server with higher capacity. 

Of course, one simple option is for you to upgrade your server. That, however, has two issues – 

Till the time you are notified of the problem and till the time you upgrade the server, your application’s user experience would remain poor. A lot of people will have negative experiences with your app/site and they may never come back. 
After the buzz from the campaign dies, the traffic would come down to the usual, and then your extra server capacity would remain idle, while you are still billed for it. 
In such situations, AWS servers offer you 2 unique solutions to automatically scale up and down your server and balance the load.

These two solutions are – 
1) Autoscaling 
2) Load Balancer. 

AWS Auto Scaling 
AWS Auto Scaling is a solution that monitors your application and automatically adjusts the capacity to make sure that you get stable and predictable performance without having to spend a lot more than is necessary

The key benefits of Amazon Auto Scaling include:
* Quick to setup scaling
* Allows making smart scaling decisions
* Application performance is maintained automatically
* Cost optimization as you pay only for the resources that you actually need.


![image](https://github.com/user-attachments/assets/54b2ac62-a84f-49a4-b97a-c199c5c7fd07)

Why Do We Need ASG?
* Automatic Scaling: Automatically adjusts the number of instances based on demand, ensuring your application can handle traffic spikes and drops.
* Fault Tolerance: Automatically replaces unhealthy instances, maintaining application performance and availability.
* Cost Efficiency: Scales down instances during low demand periods, reducing costs.
* High Availability: Distributes instances across multiple Availability Zones (AZs), enhancing application reliability.
Use Cases for ASG
* Web Applications: Automatically scale web servers to handle varying web traffic.
* Batch Processing: Scale the number of instances based on the number of jobs in a queue. 
* Big Data Applications: Dynamically scale resources for data processing tasks
* Microservices: Scale individual microservices based on their specific load requirements.
How ASG Works
ASG operates using a combination of launch templates or configurations and scaling policies. Here’s a brief overview:

** Launch Template: Defines the configuration for EC2 instances, including instance type, AMI, key pair, security groups, and other settings.
** Scaling Policies: Determine how ASG should scale in response to changes in demand. Policies can be based on metrics such as CPU utilization, network traffic, or custom CloudWatch metrics.



Practical: Setting Up an Auto Scaling Group
Step 1: Create a Launch Template
    
    ![Screenshot (1560)](https://github.com/user-attachments/assets/dc6fd913-5646-4ed1-8ad7-bfbff7c5be16)
Step 2: Configure lanuch template

![Screenshot (1561)](https://github.com/user-attachments/assets/f8990a85-b126-4a5a-8882-7a5d3a9ec1ea)

In my case I select my own AMI which i was created from the instance 

![Screenshot (1562)](https://github.com/user-attachments/assets/a0116193-36bc-405e-82a4-6df41c6658c5)

![Screenshot (1565)](https://github.com/user-attachments/assets/12c50f08-296b-492d-a859-803fa64602f2)


STEP 3: Now Create AutoScaling groups

![Screenshot (1566)](https://github.com/user-attachments/assets/ae9b10ae-3178-4824-a9b8-11ddf95163b7)

* configure the ASG

SELECT THE LAUNCH TEMPLATE WHICH IS CRETAED IN PREVIOUS STEP
![Screenshot (1568)](https://github.com/user-attachments/assets/797e7682-5877-428e-bacb-0405568f25be)

Select availabilty zones where server is used to be run

![Screenshot (1569)](https://github.com/user-attachments/assets/659c588d-006f-472b-b9f5-f4fe22aa9a27)

In mycase i choose NO load balancer.If you need LB is to be created

![image](https://github.com/user-attachments/assets/ab965b9e-1a23-4d24-9eed-5a289c883081)

Here I configure Desired capacity =1
* Desired capacity: Represents the initial capacity of the Auto Scaling group at the time of creation. An Auto Scaling group attempts to maintain the desired capacity. It starts by launching the number of instances that are specified for the desired capacity, and maintains this number of instances as long as there are no scaling policies or scheduled actions attached to the Auto Scaling group.

Minimum capacity=2
* Minimum capacity: Represents the minimum group size. When scaling policies are set, they cannot decrease the group's desired capacity lower than the minimum capacity.

Maximum capacity=6
* Maximum capacity: Represents the maximum group size. When scaling policies are set, they cannot increase the group's desired capacity higher than the maximum capacity

![Screenshot (1572)](https://github.com/user-attachments/assets/992c8765-bc73-47ab-853b-f5436352dd69)

I didn't choose Target tracking scaling policy.I select No scaling policy

TARGET SCALING POLICY IS BASED ON CPU UILIZATION.IF CPU UTILIZATION REACHES SOME STANDARDS AUTOMATICALLY NEW INSTNACES IS CREATED THROUGH AUTOSCALING GROUPS


![Screenshot (1573)](https://github.com/user-attachments/assets/ca8c438c-d0e6-47b8-ab61-179c5846509d)

AUTO SCALING GROUP IS CREATED SUCCESSFULLY

![Screenshot (1575)](https://github.com/user-attachments/assets/17571a45-c702-4c4f-becb-d36180991cd5)

TO  SERVERS ARE CREATED

![Screenshot (1576)](https://github.com/user-attachments/assets/1bd63a63-ce29-4709-9c0c-15ffc65d667d)

If suppose I deleted on server automatically it Another server is created because of ASG

![Screenshot (1578)](https://github.com/user-attachments/assets/978efc4f-2c70-4e7b-b2b0-2f6a24c09c10)

New server is created 

![Screenshot (1579)](https://github.com/user-attachments/assets/a48ff797-786d-42c6-a804-5d3614f1922e)


..................................................................................................................................................................

What is Load Balancing?
Load balancing is the distribution of workloads across multiple servers to ensure consistent and optimal resource utilization. It is an essential aspect of any large-scale and scalable computing system, as it helps you to improve the reliability and performance of your applications.

Elastic Load Balancing:
Elastic Load Balancing (ELB) is a service provided by Amazon Web Services (AWS) that automatically distributes incoming traffic across multiple EC2 instances. ELB provides three types of load balancers:

* Application Load Balancer (ALB) — operates at layer 7 of the OSI model and is ideal for applications that require advanced routing and microservices.
* Network Load Balancer (NLB) — operates at layer 4 of the OSI model and is ideal for applications that require high throughput and low latency.
* Gateway Load Balancer: Choose a Gateway Load Balancer when you need to deploy and manage a fleet of third-party virtual appliances that support GENEVE. These appliances enable you to improve security, compliance, and policy controls

Task 1:
launch 2 EC2 instances with an Ubuntu AMI IN 2 differnet availability zones
* Log in to your AWS Console and go to the EC2 dashboard.

* Click on the “Launch Instance” button and select “Ubuntu Server “.

![Screenshot (1580)](https://github.com/user-attachments/assets/d2700874-2fe1-4d2a-a5aa-39427db4c6ee)

![Screenshot (1581)](https://github.com/user-attachments/assets/f53f1072-fd92-4287-a328-b907069336a0)

![Screenshot (1582)](https://github.com/user-attachments/assets/03194876-990b-4a8e-a3dc-56f7e917ae0f)

![Screenshot (1583)](https://github.com/user-attachments/assets/bd091cb6-5087-42d1-b19f-03edc5e7f1e7)

TASK 2:

CONNECTO TO TWO EC2 INSTANCE AND INSTALL appache2 WEBSERVER AND DEPLOY SIMPLE STATIC WEBSITE

![Screenshot (1584)](https://github.com/user-attachments/assets/50aaaee6-49dd-425f-900c-0b15913b3723)

![Screenshot (1585)](https://github.com/user-attachments/assets/142af65d-7f80-43a0-88bc-a6278e245bc7)

TASK 3: 

1) UPDATE 2 SERVERS:
---
    apt update -y
---
3) INSTALL GIT AND APPACHE2 AND START webserver
---
     apt install git -y
     apt install apache2 -y && systemctl start apache2
---

  ![image](https://github.com/user-attachments/assets/7235c95b-333b-418f-95c8-673455b02456)

  
TASK 4:
   Go to inside /var/www/html path and edit index.html file (in server 1)

  ![image](https://github.com/user-attachments/assets/74a2bf1c-de76-46e6-86f3-fcc01ed20b7d)

![Screenshot (1588)](https://github.com/user-attachments/assets/d2d05545-a02f-4da1-a78c-fee80c99c245)

NOW GO TO SERVER 2 AND EDIT index.html file

![image](https://github.com/user-attachments/assets/52e9b8fd-3809-440c-abf3-a992853f10d1)

COPY PUBLIC IP OF SERVERS AND PASTE IN BROWSER 
IN FIRST SERVER :

![image](https://github.com/user-attachments/assets/e8974d13-1300-42a7-8eaa-c1d865d388c8)

IN SECOND SERVER:

![image](https://github.com/user-attachments/assets/00eeaa57-bf36-4fc5-b641-d0730caeb1c9)


TASK 5:
Create an Application Load Balancer (ALB) in EC2 using the AWS Management Console.

Log in to the AWS Management Console and go to the EC2 dashboard.

Click on “Load Balancers” in the left-hand navigation menu and then click the “Create Load Balancer” button.

Select “Application Load Balancer” as the load balancer type and click “Create”.



![Screenshot (1595)](https://github.com/user-attachments/assets/38f8b525-f62a-48df-88b0-e544e97b92b6)

![Screenshot (1595)](https://github.com/user-attachments/assets/9eb867d9-ed2d-43b6-a505-e8cc2e493eaf)

CHOOSE AVAILABILITY ZONES AS ap-south-1a (aps1-az1) AND ap-south-1b (aps1-az3) (Becuase while creating instances we cretaed in different availability zones 1a and 1b)


![Screenshot (1597)](https://github.com/user-attachments/assets/a391d174-2a9d-4f47-a24d-5699cb188840)

CLICK ON CREATE TARGET GROUPS:

![image](https://github.com/user-attachments/assets/6a4d5b06-7344-4b46-b398-8a27011c2488)

![image](https://github.com/user-attachments/assets/befb3f78-9d23-40cc-abc9-812f67255ed3)


SELECT REGISTER TARGETS

![image](https://github.com/user-attachments/assets/e7d8e18b-5251-4321-a713-7ae6ce2c6ae7)

CLICK ON INCLUDE PENDING AS BELOW

![image](https://github.com/user-attachments/assets/0fb43763-900e-41c8-8974-61319c4a6744)

CLICK ON CREATE TARGET GROUPS

TARGET GROUP IS CREATED

![image](https://github.com/user-attachments/assets/26eaa74a-07c4-42ad-959b-eb7bc9be0277)

NOW SELECT THE TARGET GROUPS IN LOAD BALNCER CONFIGURAION

![image](https://github.com/user-attachments/assets/045c7ca0-d0a6-41b0-b377-cdce9ae649d7)

LOAD BALNCER IS CREATED

![image](https://github.com/user-attachments/assets/6e09324e-f4dd-4971-a700-464280173d5d)


NOW COPY THE DNS OF LOAD BALANCER AND PASTE IN BROWSER

MYLB-378597800.ap-south-1.elb.amazonaws.com

![Screenshot (1606)](https://github.com/user-attachments/assets/f4819e6a-b1c1-46ae-8063-28d197a4cb8d)

![Screenshot (1607)](https://github.com/user-attachments/assets/6ce56c79-ecd1-49a5-8e95-c2f9c675563e)


.............................................     LOAD BALANCER IS CONFIGURED SUCCESSFULLY .........................................................


