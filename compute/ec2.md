
# Page contents

## Introduction

This is done to give you an idea about what the EC2 service is and what it can be used for.

[[#What is an EC2 instance?]]
[[#What is a virtual machine]]
[[#What is the use case for the EC2 service?]]
[[#Instance types]]
[[#What operating systems can you use?]]
Graviton VS x86: Processor wars
Instance storage
Security groups
Public IP/Elastic IPs and Private IP addresses
Nitro System
Autoscaling
launch templates

Links to other documents that are used alongside the EC2 service:
[[EBS]]
VPC
Route 53
## Diagrams for setups 

Some Projects I have worked on and it can give you an idea about how some of the topics we have talked about in the Introduction work with each other.

A simple Minecraft Server

Simple apache webserver for a website

Loadbalance apache servers if there was more load

Loadbalance a wordpress site with RDS and route53 - 

Autoscaling to scale in and out if needed.

Monitoring the instances at scale.
## Edgecases

Things I don't normally see but they are nice to know incase they are needed in the future.


## What is an EC2 instance?

When I think of the word EC2 my first thought is a virtual machine.

### What is a virtual machine

A virtual machine is a way where you can split up the resources that you PC has (The CPU, Memory and storage) and you are splitting it so that it can run another OS on your computer you can view this as a virtual computer - A lot of people use them day to day - To have a ton of servers from one massive server, To test and do dev work on a VM on your personal machine, For security because you can think of a virtual machine as it own thing if there is a virus or malware it is unlike to escape the virtual machine but it can happen.

Now that we know that a virtual machine is a virtual computer we now  have a basic understand of what EC2 is it is a virtual machine service but how and why would we use this service?

## What is the use case for the EC2 service?

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

## Instance types




Instances don't come in one type there are multiple - Here are the types and the use cases around them:

<ul>
  <li><b>General Purpose</b> - This is suited for open source apps, gaming servers, microservices - It is General Purpose because it tries to strike a balance For CPU and RAM - The M seires, MAC and T2,3,4 are in this group.
  </li>
  <li><b>Compute Optimised</b>- This is suited for tasks that require a lot of compute the weight for the instance type are less memory but the same amount of Vcpu </li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>

</ul>
To read into the topic more or get information around Instance types check this <a href="https://aws.amazon.com/ec2/instance-types/">link</a>

## What operating systems can you use?

## Nitro System
