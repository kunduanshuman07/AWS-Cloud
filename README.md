# AWS-Cloud
Copyright @Anshuman Kundu

## Table of Content:

# Table of contents

- **Chapter I : AWS Cloud Practitoner**

  - [Networking Terminologies](#networking-terminologies)
  - [Protocol](#protocol)
  - [IP Address](#ip-address)
  - [PORT](#port)
  - [Client Server Architecture](#client-server-architecture)
  - [Classic Data Centers](#classic-data-centers)
  - [Virtualization](#virtualization)
  - [Cloud Computing](#cloud-computing)
  - [Cloud Computing Deployment Models - Public/Private/Hybrid/Community](#cloud-computing-deployment-models---publicprivatehybridcommunity)
    - [Public Cloud](#public-cloud)
    - [Private Cloud](#private-cloud)
    - [Hybrid Cloud](#hybrid-cloud)
    - [Community Cloud](#community-cloud)
  - [Cloud Computing Service Models - IaaS/PaaS/SaaS](#cloud-computing-service-models---iaaspaassaas)
    - [IaaS](#iaas---infrastructure-as-a-service)
    - [PaaS](#paas---platform-as-a-service)
    - [SaaS](#saas---software-as-a-service)
  - [AWS Regions](#aws-regions)
    - [How to choose AWS Regions?](#how-to-choose-an-aws-region)
  - [AWS Availability Zones](#aws-availability-zones-az)
  - [IAM : Identity and Access management](#iam--identity-and-access-management)
    - [IAM - Policies](#iam---policies)
    - [IAM - MFA](#iam---mfa)
    - [IAM - Roles](#iam---roles)
    - [IAM - Security Tools](#iam---security-tools)
  - [AWS Access keys, CLI and SDK](#aws-access-keys-cli-and-sdk)

# Networking Terminologies:

1. Network is a set of 2 or more computers connected to each other for sharing resources.
2. The connection between the computers can be made using a cabel, telephone lines, radiowaves, satellites, etc.

**Analogy: Consider an example of a sender (1st computer) who wants to send a letter (file) which is 10 pages long to the recipient (2nd computer).**

1. The only available envelope size can accomodate only 1 page of that letter which will lead to create 10 envelopes to accomodate the 10 page long letter with page sequence and recipient address written on each page. This is called breaking down the file or the data or the sharing resource into smaller chunks with sequence number and recipient address.
2. Now the 10 envelopes will be given all at once to the post office (Gateway or ISP) which will then start delivering the envelopes to the recipient address. The envelope with the sequence number and the recipient address is termed as a Datagram. The recipient will recieve the envelopes and will arrange the letter pages according the sequence number written on it.

This is exactly how communication happens between computers in a network.

# Protocol

1. A set of rules or standards which defines a language for the communication between computers in a network.
2. Most common used protocols are **TCP (Transmission Control Protocol)** & **UDP (User Datagram Protocol)**.

**UDP:**

Consider the exmaple above. In that exmaple when the 1st computer sends the 10 chunks of data, there can be lots of possibilities where data can be lost and not delivered correctly. In this case the 2nd computer will request the missing chunks of data again from the 1st computer and then will retrive it. This is called **User Datagram Protocol** where the reciever is unware of the data coming to it unless it starts recieving it. This is connectionless because no connection is built between the sender and the reciever. 

**TCP:**

But UDP is not safe for sensitive data which needs to be correctly delivered. There comes **Transmission Control Protocol** where before starting to send the data a prior connection is established between the sender and the recipient. After the connection is built, the sender sends the 1st sequence data to the reciever. Once its recieved, the reciever sends an acknowledgement back to the sender. The sender only after recieving the acknowledgement continues sending the other data in the sequence.

# IP address

A 32 bit integer ocatves which looks like 0-255.0-255.0-255.0-255 where every octave can contain any number from 0-255, uniquely identifies the computer and helps connect your computer in any network. When data is sent from the 1st computer, the IP address of the 2nd computer helps the ISP to find out the machine matching with the address and directs your data to that specific machine.

# PORT

A 16 bit integer ranging from 0-65525 which acts as the endpoint of the gate to the specific application to reach in a specific machine. So basically you being the 2nd computer is asking some data from the 1st computer over the internet. The data being sent to you will find out your machine via IP address but there are lots of applications running on a single machine OS, the data is needed by you sitting on one of the applications in the machine. So, the PORT number will decide which application data should be delivered to.

# Client Server Architecture

Client is the computer requesting some data(request) and Server is the computer serving the data (response). 

Consider one scenario below:

1. Server Setup:

Three computers, each with its own IP address, are connected to the switch. The switch is a device which learns the MAC addresses of these computers and which ports they are connected to by the incoming request frames/ip packets from the client computer.
Each computer here will called a server.

2. Client Request:

Your computer wants to request data from one of the servers. Your computer sends an IP packet to the router if the server is on a different network, or directly to the switch if it's on the same network.

3. Router's Role:

If the server is on a different network, the router will determine the best route for the packet and forward it to the correct network.

4. Switch's Role:

The switch receives the packet and looks at its MAC address table.
If the destination MAC address is in the table, the switch forwards the frame to the correct port.
If the destination MAC address is not in the table, the switch floods the frame to all ports (except the incoming port) until it learns the correct port.

5. ARP Operation:

If your computer knows the server's IP address but not its MAC address, it sends an ARP request to the local network.
The server responds with its MAC address.
Your computer and the switch then use this MAC address to direct future frames to the server.

6. Server Response:

The server processes the request and sends a response.
The response is directed to your computer's MAC address.
The switch forwards the frame to your computer's port based on its MAC address table.

# Classic Data Centers

Staring an IT Business requires a Physical IT infrastructure. This infra will contain hardwares which will decide your computational power, databases which will store data for you and network entities to decide your networking capabilities. This physical infrastructure defining compute, storage and network is called a Data Center. Then you will run Operating systems (computers) and applications to serve to users on top of the OS eventually using the physical infrastructure abilities.

## Problems with classic data centers:

1. Upfront cose to establish the physical infrastructure.
2. Cost for power, maintenance, cooling, etc.
3. Disaster recovery.
4. Security and Survillance.
5. Scalability
6. Upgrades
7. Hardware Replacements

# Virtualization 

Let suppose we have built a physical system which only contains the hardware and the operating system. Now instead of running a single machine, we created virtual machines which will have the desired OS and desired applications can be run on it and at the same time serveral othe virtual machines can also be created and used be several other users at the same time. These machines will use the single physical system of rescources instead of creating the complete package for every single user.

## Key properties:

1. Isolation: Every machine is isolated from one another.
2. Partitioning: Machines are partitioned with there own set of OS and requirements.
3. Provisioning and Migrating will not be an issue because you are not involved in hardware level things. You just need to care about the OS and the application you make and use in the VM.
4. Encapsulation of all the things you do in a single isolated place.
5. No upfront cost and paying for only what you want.

# Cloud Computing

A collection of computing resources which can be accessed via the internet and provided to the users on demand.

## Need of Cloud Computing

1. Cost effective
2. Scalable
3. Elastic
4. High availabilty
5. Security
6. Flexibility

# Cloud Computing Deployment Models - Public/Private/Hybrid/Community

## Public Cloud

**Definition**:
Public clouds are cloud environments owned and operated by third-party cloud service providers, which deliver computing resources like servers and storage over the internet.

**Characteristics**:
Scalability: Resources can be scaled up or down quickly to meet demand.
Cost-Effective: Users only pay for the resources they use.
Maintenance-Free: The cloud provider manages and maintains the infrastructure.
Accessibility: Resources are available over the internet, making it accessible from anywhere.

**Examples**:
Amazon Web Services (AWS)
Microsoft Azure
Google Cloud Platform (GCP)

## Private Cloud

**Definition**:
Private clouds are cloud environments dedicated to a single organization. They can be physically located on the company’s on-site datacenter or hosted by a third-party service provider.

**Characteristics**:
Security: Provides enhanced security and privacy as resources are not shared with other organizations.
Customization: Can be tailored to the specific needs of the organization.
Control: The organization has complete control over the infrastructure and data.
Compliance: Easier to meet regulatory and compliance requirements.

**Examples**:
VMware Cloud
OpenStack

## Hybrid Cloud

**Definition**:
Hybrid clouds combine public and private clouds, allowing data and applications to be shared between them. This provides businesses with greater flexibility and more deployment options.

**Characteristics**:
Flexibility: Can run applications and store data where it makes the most sense.
Cost Optimization: Sensitive workloads can be kept on private clouds, while less-critical resources can be run on public clouds.
Scalability: Can use public cloud resources to handle bursts of traffic.
Integration: Requires sophisticated technology to integrate both cloud environments seamlessly.

**Examples**:
IBM Hybrid Cloud
AWS Outposts

## Community Cloud

**Definition**:
Community clouds are cloud environments shared by several organizations with common concerns (e.g., security, compliance, jurisdiction).

**Characteristics**:
Collaboration: Facilitates collaboration among organizations with similar needs.
Cost Sharing: Costs are spread across the organizations, making it more cost-effective than a private cloud.
Compliance: Easier to comply with industry-specific regulations.
Managed by Third Party or Organizations: Can be managed by the participating organizations or by a third-party provider.

**Examples**:
Government clouds for different departments
Healthcare clouds for various healthcare providers

# Cloud Computing Service Models - IaaS/PaaS/SaaS

**Components**:
1. Networking
2. Storage
3. Servers
4. Virtualization
5. O/S
6. Middlewares
7. Runtime
8. Data 
9. Application

## On premise Infrastructure

Let us take an example of buying a car. You are responsible for everything associated with the car, where to store the car, the fuel and its capacity, its maintenance, etc. Similarly on an On premise infra you have to manage everything and take care of all the components listed above.

## IaaS - Infrastructure as a Service

If you visit Goa and want a car for 7-8 hours, then instead of buying it you just rent the car and pay for what and how much you use and maitain the car. Therefore you are using the car as a infrastructure and not really care about how is it built and who does it belong to. Similarly in IT IaaS you are responsible for everything except the hardware i.e Networking, Storage, Servers, Virtualization.
**Example: Virtual Machines**

## PaaS - Platform as a Service

If you prefer not to manage a car at all, you can book a cab service for pick-up and drop-off. You use the car as a platform and don't worry about the car's maintenance. Similarly in IT PaaS you are responsible for the Application and the Data and not the platform for developing the application.
**Example: AWS Elastic Beanstalk**

## SaaS - Software as a Service

If you donot care about anything related to the transport and you only care about reaching a certain place you just take a public transport.
Therefore you are using the transport as a Service. Similarly in IT SaaS you are responsible for using the software and dont care about how and where is it built.
**Example: Gmail**

# AWS Regions

Region is a geographically large area which contain a cluster of Data Centers. There are a variety of regions where AWS has put their data centers.
**Example: us-east-1, eu-west-3, etc.**

**Most of the AWS services are Region scoped (But their are global services as well) i.e they run within the region and if we want to run the same services in another region, it will entirely different and new.**

## How to choose an AWS Region?

*If you want to run a new application in AWS, in which region you should do it?*
It depends on below parameters:

1. **Compliance** : Data can never leave a region without explicit permissions i.e if you are storing French people data in France Region and the same data is required in Asia region then both French and Asian Governments will come in picture and provide necessary permissions only if its not going to effect anything and it's okay. Therefore legalities come in picture before choosing any AWS Region.

2. **Proximity** : If most of your application users are in America and you deploy your application in Australia region then users from America will have increased latency. Therefore you should choose your region close to your users.

3. **Available Services** : Not all regions contain all AWS services. Therefore choose regions where your application's services are available.

4. **Prices** : It varies according to regions. Therefore check your service price before choosing regions.

# AWS Availability Zones (AZ)

AZ's are phycially large and discrete locations within regions containing one or more data centers. Ther are designed to avoide service failure during disasters. Every AZ in a region are very far with each other to avoid calamatic failure but are connected with very low latency and high badwidth.

**A region can have minimum of 3 and maximum of 6 AZ's**.

# IAM : Identity and Access management

IAM is a global service. When we created the AWS account, all our credentials belongs to the root user. But if we want different users within the same organization to use that account's services , we should not expose root user credentials rather we should create groups and put users on those groups.

**Important points**:

1. *Every group that you create will have its own set of permissions and every user inside that group will abide by those persmissions.*
2. *Groups can only contain users and not other groups i.e groups cannot be nested.*
3. *Users does not necessary need to belong to a particular group.*
4. *A single user can belong to multiple groups.*
5. *Users or groups can be assigned JSON documents called policies.*
6. *Policies define the permissions for them i.e what services they can use and upto what extent (what all operations they can perform using allowed services).*

## IAM - Policies

**IAM Policy inheritance**

Let suppose there is a group developers with 2 users A and B with Policy x attached to it. There is a second group clients with users C and D with policy y attached to it. There is a third group testers with users B and C with a Policy z attached to it.

Summary of users, groups and policies:
| User | Group | Policy |
|------|-------|--------|
| A | developers | x |
| B | developers, testers | x, z |
| C | clients, testers | y, z |
| D | testers | y |

*We can see that user B and C being in two different and one common groups inherited the policies from other groups as well.*

**IAM Policy structure**

JSON format

```js
  {
    "Version": "2021-10-17", // This is the policy language version which always includes 2021-10-17
    "Id": "S3-Account-Permissions", // This is the unique id associated to the policy (optional)
    "Statement": [ // Statements consists of the below parameters
      {
        "Sid": 1, // Statement id (optional)
        "Effect": "Allow" // It can be Allow or Deny depending upon whether you want to give the access of refrain it
        "Principal":"arn:aws:user:19785754567876", // The account, user, role you want the policy to apply
        "Action": [ // List of actions on which the policy allows or denies
          "s3: GetObject",
          "s3: PutObject
        ],
        "Resource": [ // List of resources on which the policy allows or denies
          "S3::bucket:arn..."
        ]
      }
    ]

  }

```
## IAM - MFA

**Policy Password**

You can give own set of rules for creating passwords of a policy, role, user, group, etc. which provides additional security level.

**MFA: Multi Factor Authentication**

Your password + security token provided by a device you own combines to form a MFA. It creates a high level security for your AWS account. Although somebody hacks your password, he will not be able to get inside the account because MFA asks for the device token which you have configured and this token changes every other second. Therefore this adds another level highly secure AWS system.

Token provider example: ***Google Authenticator***

## IAM - Roles

Let suppose we created an EC2 instance and when we started it, it may want to do some inital things such as to read some file, etc. To do so we attach the service with an IAM role which has perimissions for actions the services attached to it can perform. Therefore the EC2 instance and the IAM role attached to it act as a single entity i.e on behalf of you the services can work by searching the required permissions from the attached IAM role instead of asking persmission from you everytime.

## IAM - Security Tools

1. IAM Credential Report : This generates a report with all your account's users with their credentials.
2. IAM Access Advisor: This provides a report with all users service permissions and last time those services were accessed by the specific user.

# AWS Access keys, CLI and SDK

You can access all the services of AWS using AWS Management console, CLI or Software Development Kit(SDK).
AWS Management console involves password + MFA, CLI and SDK uses access keys to secure your AWS account.
CLI is a cloud line interface which used access keys and MSI CLI installer to be set up in your local for accessing AWS services wheras SDK's are software application embedded in your application which uses programming languages to access your AWS account, you can access AWS services from both.


