# Page contents

# Introduction

This is done to give you an idea about what the EC2 service is and what it can be used for.

- [What is an EC2 instance?](#what-is-an-EC2-instance)
- [What is a virtual machine?](#what-is-a-virtual-machine)
- [What is the use case for the EC2 service?](#what-is the-use-case-for-the-EC2-service)
- [Instance types](#instance-types)
- [What operating systems can you use?](#what-operating-systems-can-you-use)
- [Graviton VS x86: Processor wars](#AWS-Graviton-VS-x86:The-great-processor-wars)
- [Instance storage](#instance-storage)
- [Security groups](#security-groups)
- [Public IP/Elastic IPs and Private IP addresses](#public-IP/Elastic-IPs-and-Private-IP-addresses)
- [Nitro System](#)
- [Autoscaling](#)
- [launch templates](#)
- [Loadbalancing]()
- [Burst balance]()

Links to other documents that are used alongside the EC2 service:

- [EBS]()
- [VPC]()
- [Route 53]()

# Diagrams for setups

Some Projects I have worked on and it can give you an idea about how some of the topics we have talked about in the Introduction work with each other.

- [A simple Minecraft Server]()

- [Simple apache webserver for a website]()

- [Apache servers if there was more load]()

- [Loadbalance a wordpress site with RDS and route53](#)

- [Autoscaling to scale in and out.]()

- [Monitoring the instances at scale.]()

## Edgecases

Things I don't normally see but they are nice to know incase they are needed in the future.

## what-is-an-EC2-instance

When I think of the word EC2 my first thought is a virtual machine.

## what-is-a-virtual-machine

A virtual machine is a way where you can split up the resources that you PC has (The CPU, Memory and storage) and you are splitting it so that it can run another OS on your computer you can view this as a virtual computer - A lot of people use them day to day - To have a ton of servers from one massive server, To test and do dev work on a VM on your personal machine, For security because you can think of a virtual machine as it own thing if there is a virus or malware it is unlike to escape the virtual machine but it can happen.

Now that we know that a virtual machine is a virtual computer we now have a basic understand of what EC2 is it is a virtual machine service but how and why would we use this service?

## what-is-the-use-case-for-the-EC2-service

The EC2 Service has many use cases I will list some examples I have created myself.

<ol>
   <li>Creating Game servers - In the past I have created Minecraft servers, Valhelm servers and 7 days to die servers - This is done so that I could play with friends but you could open the server up to the world or if you was making your own game you could host the server or servers using the EC2 service.
   </li>
	 <li>Web hosting - if you was hosting your website using apache you could use EC2 to host your website - This would be great if you have a website that needs to use apache or some other application for web hosting
	 </li>
	 <li>
		   Self-hosted applications - There might be applications that you would want to self-host for example gitlab, jenkins, Monitoring and more.
	 </li>
</ol>

## instance-types

Instances don't come in one type there are multiple - Here are the types and the use cases around them - This list is from 2024:

Instances can come in many different shapes and sizes a M6g is different from a M6i due to the processor so I will be breaking down the latter part of an instance name so that you know what the g and i mean in M6 and the other instance types
### Additional Capability
#### Processor families
- **i** - This means it is an intel based processor, You will normally see this if you have multiple options for example if you can choose a AWS Graviton Processor or an AMD Processor. This is importent if you care about performance, Cost and if you application can be used on an ARM based processor.
- **a** - This means it is an AMD based processor, This is normally a cheaper option then using an intel based processor but in benchmarks Intel tends to performs better but if you need a cheap x86 alternative then AMD is normally a option - It might be that you have tested a machine in production and you don't actually need the additional performance so you might rightsize to AMD instead to save a bit on costs.
- **g** - This means this is using an AWS Graviton Processor - This is an arm based processor and it is normally the cheapest option and provides the best price to performance - The reason for this is due to the fact that AWS are moving towards ARM based processors due to the amount of energy they use and price to performance that comes with using a graviton processor. 
#### Additional capabilities
- **b** – EBS optimized
- **d** – Instance store volumes
- **n** – Network and EBS optimized
- **e** – Extra storage or memory
- **z** – High performance
- **q** – Qualcomm inference accelerators
- **flex** – Flex instance

- **General Purpose** - This instance type tries to strike a balance between CPU and RAM<br> **USE CASES** - This is suited for **open source apps**, **gaming servers**, **microservices**<br>**Instance family names** - The **M series**, **MAC** and **T2,3,4** are in this group.
  !["Image of all the EC2 option in the following order - M7g,M7i,M7i-flex,M7a,MAC,M6g,M6i,M6in,M6a,M5,M5n,M5zn,M5a,M4,T4g,T3,T3a,T2"](./pictures/EC2/GP_instance_types.png)
- **Compute Optimised** - This is suited for tasks that require a lot of compute the weight for the instance type are less memory but the same amount of Vcpu.<br>**USE CASES** - This is suited for **High performance computing(HPC)**, **Batch processing**, **Ad serving**, **Video encoding**, **Gaming** **scientific modelling**, **distributed analytics**,**CPU based machine learning**<br> **Instance family name** - The **C series** are in this group.
  !["Image of all the EC2 option in the following order - C7g,C7gn,C7i,C7a,C6g,C6gn,C6i,C6in,C6a,C5,C5n,C5a,C4"](./pictures/EC2/Compute-instance-types.png)
- **Memory Optimised** - This is suited for tasks that require a lot of memory the weight for the instance type are more memory but less amount of Vcpus.<br>
  This is suited for **Open-source databases**,**in-memory caches**,**Real-time big data analytics In-memory databases (e.g. SAP HANA, Redis) traditional databases (e.g. Oracle DB, Microsoft SQL Server), and in-memory analytics (e.g. SAS, Aerospike).** <br>
	**Instance family name R, X, Z** and **High memory** are in this group.


- **Accelerated Computing** - - This is suited for tasks that require a GPU (Graphic processing unit) or hardware accelerators, or co-processors - This is due to that the fact that they can carry out the following tasks - floating point number calculations, graphics processing, or data pattern matching - This is works better on dedicated hardware then your CPU. <br>
  This is suited for **Generative AI applications, including question answering, code generation, video and image generation, speech recognition,**  **Android game streaming, machine learning inference, graphics rendering, autonomous vehicle simulations** and more.
  
- **Storage Optimized**

- **HPC Optimized**

To read into the topic more or get information around Instance types check this <a href="https://aws.amazon.com/ec2/instance-types/">link</a>

## what-operating-systems-can-you-use
You can use 100s of operating systems - Would you like to use arch linux - There is an AMI (Amazon Machine Image) you can spin up - You want to use fedora server or ubuntu they have an ami for them as well - Notice how I mentioned different linux distributions there are many flavours of linux and on AWS that is no different from ubuntu to red hat to oracle there are many images for a distribution you need.

Windows server is also an option if you need to host an active directory server and you do not want to use a service like AWS directory you could create a 
## AWS-Graviton-VS-x86:The-great-processor-wars

## instance-storage

## security-groups

## public-IP/Elastic-IPs-and-Private-IP-addresses

## Nitro System

## Autoscaling

## launch-templates

## Load-balancing

## Burst-balance