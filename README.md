## Title: Building a Cybersecurity Home Lab for in-depth investigation and threat hunting with AWS Services Using Terraform

## 1.0	Background Overview
The recent development in IT industry has necessitated the use of necessary technology and tools to achieve the result. This is not limited to the use of Infrastructure as Code in automating security systems at every stages.  This project focuses on using Terraform to provision and configure a homelab environment on AWS Cloud with AWS services for in-depth investigation and threat hunting. The homelab includes two victim workstations, and one for Blue Team (defending the environment), one for Red Team (simulating attackers). The goal is to simulate cybersecurity scenarios for learning and testing incident detection, response, and remediation techniques.

## 1.0	Introduction
As the world becomes increasingly digital, the frequency and sophistication of cyberattacks continue to rise, making it crucial for cybersecurity professionals to stay ahead of emerging threats. In-depth investigation and threat hunting are vital practices for identifying, analyzing, and mitigating potential security incidents within any network or cloud environment. To effectively train and test cybersecurity skills, hands-on experience with real-world scenarios is essential. This project focuses on building a comprehensive cybersecurity home lab that simulates both attack and defense environments using AWS services and Infrastructure as Code (IaC) principles via Terraform.
The lab is designed to replicate the dynamics of a real-world enterprise network, consisting of two workstations: one for the Blue Team, tasked with defending the environment, and one for the Red Team, simulating malicious attackers. The Red Team workstation is equipped with tools and frameworks to emulate various types of cyberattacks, including penetration testing and exploit simulations. On the other hand, the Blue Team workstation is configured with various monitoring, detection, and response tools, enabling the detection and mitigation of simulated threats in real time.
By leveraging Terraform, a powerful IaC tool, the entire infrastructure can be provisioned, configured, and maintained in an automated, repeatable, and consistent manner. Terraform allows for the dynamic creation of resources in AWS, including EC2 instances, security groups, IAM roles, and networking setups. This project utilizes a variety of AWS services such as EC2 for virtual machines, S3 for storage, VPC for networking, and CloudWatch for monitoring and log analysis. The combination of Terraform and AWS services enables an efficient, scalable, and cost-effective environment that mirrors real-world cybersecurity challenges.


The primary objective of this lab is to create a realistic and interactive environment for simulating cybersecurity incidents, which can be used for training, research, and skill development. The home lab environment is purposefully designed with distinct components, including: 

•	Two victim workstations for threat simulations and two team-specific setups.

•	Blue Team Workstation: Focused on monitoring, detecting, and responding to malicious activities.

•	Red Team Workstation: Simulating advanced persistent threats (APTs), penetration testing, and attack vectors.

This lab provides a hands-on platform for executing and analyzing real-world scenarios, such as network intrusions, malware attacks, and incident response workflows. The incorporation of AWS services enhances the scalability and reliability of the lab, while Terraform ensures rapid deployment and teardown of environments, promoting repeatability and experimentation.


What is Terraform?
Terraform is an infrastructure as code tool that lets you build, change, and version cloud and on-prem resources safely and efficiently.
HashiCorp Terraform is an infrastructure as code tool that lets you define both cloud and on-prem resources in human-readable configuration files that you can version, reuse, and share. You can then use a consistent workflow to provision and manage all of your infrastructure throughout its lifecycle. Terraform can manage low-level components like compute, storage, and networking resources, as well as high-level components like DNS entries and SaaS features.

The providers are publicly available on the Terraform Registry, including Amazon Web Services (AWS)and others including Azure, Google Cloud Platform (GCP), Kubernetes, Helm, GitHub, Splunk, DataDog, and many more. (https://registry.terraform.io/browse/providers)

 

The core Terraform workflow consists of three stages:

•	Write: You define resources, which may be across multiple cloud providers and services. For example, you might create a configuration to deploy an application on virtual machines in a Virtual Private Cloud (VPC) network with security groups and a load balancer.

•	Plan: Terraform creates an execution plan describing the infrastructure it will create, update, or destroy based on the existing infrastructure and your configuration.

•	Apply: On approval, Terraform performs the proposed operations in the correct order, respecting any resource dependencies. For example, if you update the properties of a VPC and change the number of virtual machines in that VPC, Terraform will recreate the VPC before scaling the virtual machines.



## 2.0	Project Objective
•	Automate the deployment of infrastructure using Terraform as an Infrastructure as Code (IaC) tool.

•	Provide a controlled environment for exploring cybersecurity concepts like monitoring, intrusion detection, and incident response.

•	Develop a scalable cybersecurity home lab on AWS to simulate real-world threat detection, response, and mitigation scenarios.

Project Goals
1.	Automate the setup of a cybersecurity lab with AWS resources.
2.	Integrate tools for red and blue team activities.
3.	Simulate realistic attack scenarios and document response processes.
4.	Analyze and log network traffic for security analysis.


Scope
The lab will be capable of supporting:
•	Blue Team Activities: Defensive tasks like monitoring, detecting threats, and analyzing logs.
•	Red Team Activities: Offensive techniques such as penetration testing and simulated attacks.


## 3.0	Project Requirements and Technical Tools
The tools required for this project include the following:

•	Virtual machine: Windows 10 installed on VirtualBox (run a powershell script to configure the ADLAB machines)

•	An AWS Account: Create  AWS Free Tier account 

•	AWS Cli installed

•	Terraform configuration files (Source : https://github.com/Samuel-Adeola/PurpleTeam_Cloud_Lab)

•	Terraform Setup: Install and configure Terraform for AWS by setting up AWS CLI and access credentials.



## 4.0	Methodology
Virtual machine: Windows 10 installed on VirtualBox
Installation
•	To install, you will need to follow these steps:

•	AWS Account: Create  AWS Free Tier account with the required resources EC2 (For deploying workstations - Blue Team, Red Team, and victim machines), VPC (For creating isolated networking environments), IAM (AdminFullAccess), Security Groups, key Pair, AWS Command Line Interface (CLI). 

•	(AWS Free Tier Account - https://aws.amazon.com/free/compute/?p=ft&z=subnav&loc=3)

•	create a user with administrator permissions and get its ACCESS KEY and SECRET KEY

•	Switch to eu-west-1 region in your aws console (on the browser)

•	Go to EC2 --> Instances --> Key Pair and create a key with name ec2_key_pair (All lowercase) and save the .pem key file.

•	Copy your ec2_key_pair.pem file to your C:\Users\<your username>\.ssh folder and rename it to id_rsa

•	AWS Cli installed

 

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

•	Terraform configuration files downloaded and copied to any folder in %PATH% Environment (Source : https://github.com/Samuel-Adeola/PurpleTeam_Cloud_Lab) 

•	Open the command prompt (cmd) and run aws configure  

•	Provide the ACCESS KEY, SECRET KEY, the region as eu-west-1

•	Open cmd again, go to the PurpleTeam lab directory (this project folder)
•	run: terraform init and then terraform apply --auto-approve

•	This will  40 mins to complete. The Purple team lab will be created in AWS. 

•	To destroy, run terraform destroy --auto-approve


Note: Just a reminder, keeping it running will cost you money.
To change to prefer the region, update the main.tf file and change the region and create an ec2_key_pair in the region you choose as these are not transferrable between regions.

## 5.0	Result:
# 5.1 Step 1: AWS Setup
5.1.1 AWS Account: Create  AWS Free Tier account with the required resources EC2 (For deploying workstations - Blue Team, Red Team, and victim machines), VPC (For creating isolated networking environments), IAM (AdminFullAccess), Security Groups, key Pair, AWS Command Line Interface (CLI). 

(AWS Free Tier Account - https://aws.amazon.com/free/compute/?p=ft&z=subnav&loc=3)
5.1.2 Create AWS Full administrative Access for user in IAM

![AWS Fig2](https://github.com/user-attachments/assets/1ea12618-d1ac-4683-9489-035293f3f6f2)


![AWS Fig5](https://github.com/user-attachments/assets/165fc6f8-d645-4e9e-b1f9-05de61bd06e8)



To create Access Key:

![AWS Fig8](https://github.com/user-attachments/assets/3dbf7c90-afe8-4ea7-9dea-dc4eaa9955ee)


 ![AWS Fig9](https://github.com/user-attachments/assets/2a7c334d-f90f-4742-88cd-9d6f1de8af5e)



Access key and Secret access key created. These keys should be save and will be used in the future:



![AWS Fig11](https://github.com/user-attachments/assets/08826404-ebc1-43ff-bbd1-b2e2965dabdd)



![AWS Fig12](https://github.com/user-attachments/assets/519aec59-8095-459b-b772-c0bb0cf0c7e3)




5.1.3	Create Key pair
Search for ec2. On the dashboard, select Keypair under the Resources



![AWS Fig13](https://github.com/user-attachments/assets/1a407edb-e244-459c-831c-3cf47d532d45)



![AWS Fig15](https://github.com/user-attachments/assets/638eb070-17af-4fd1-8889-de8c7295cf2a)



Keypair – ec2_key_pair was created in the Downloads folder. Select the Downloads:

![AWS Fig17](https://github.com/user-attachments/assets/8eb0fe0a-2f09-430e-a090-e4d653a5938a)



Created a folder named “.ssh” in C:\Users\samar



![AWS Fig18](https://github.com/user-attachments/assets/83adabf1-7211-44d6-b8ba-677b2570162a)

 

 

Save the Key – ec2_key_pair in .ssh folder 

![AWS Fig19](https://github.com/user-attachments/assets/f6c2e7ca-c6f6-4665-a1a3-61a0274424e7)



Rename the “ec2_key_pair” to id.rsa


![AWS Fig20](https://github.com/user-attachments/assets/09298669-6913-40a1-9d34-45d10ef814d1)


5.1.3 – Installing AWS Command Line Interface
Browse 
Scroll down to Windows  and copy the command:


![AWS Fig21](https://github.com/user-attachments/assets/183f6cb7-831a-4e1c-a7b7-fd9e0a38d453)


Paste the command in the CMD

![AWS Fig22](https://github.com/user-attachments/assets/d617f5f1-48e1-4f25-8819-ff8318aa3ad8)


![AWS Fig23](https://github.com/user-attachments/assets/8c24608a-a04a-4073-9307-6b584dcfdaeb)


![AWS Fig24](https://github.com/user-attachments/assets/d3981254-06cf-453d-9f28-703cbc7584a2)



![AWS Fig26](https://github.com/user-attachments/assets/66703f73-c7f2-4cb7-b810-ebde7147da57)



AWS CLI successfully installed:

![AWS Fig29](https://github.com/user-attachments/assets/2e2d4d66-bdf5-48e9-83a0-0dd531b54d49)


Input the Access key and Secret access key previously generated


![AWS Fig30a](https://github.com/user-attachments/assets/e60d9b1c-1af3-4524-9844-b9015af4a91d)



# 5.2 Terraform Installation
Steps to install 

![Terraform Fig1](https://github.com/user-attachments/assets/e8a92543-da73-4e0a-bef7-3920ac36fb99)



Terraform downloaded for Windows from


![BlueTeamFig2](https://github.com/user-attachments/assets/a253f29c-1a43-4416-a287-b35e1591dd84)



Terraform.exe extracted and save in Created a folder named “terraform” in C:\Windows


![Terraform Fig4](https://github.com/user-attachments/assets/7db88af3-79c8-4559-85d4-0ae1ec26165d)



5.2.2	Download Terraform configuration files https://github.com/Samuel-Adeola/PurpleTeam_Cloud_Lab

![Terraform Fig5](https://github.com/user-attachments/assets/89139aa1-1b70-4b7b-aec0-917721a77b31)


![Terraform Fig6](https://github.com/user-attachments/assets/59d36f64-3fc8-4fda-b107-2e591341ab49)



![Terraform Fig7](https://github.com/user-attachments/assets/9e2daff6-28b8-4fcf-8d13-cf6308d63752)


![Terraform Fig8](https://github.com/user-attachments/assets/58d6cb11-3696-443e-a49b-94f4fcdc4186)



![Terraform Fig8a](https://github.com/user-attachments/assets/c2471837-a47f-4137-9da6-97516932693b)




 
5.2.3	Run Terraform configuration files 
Open cmd and navigate to terraform configuration files location


![Terraform Fig9](https://github.com/user-attachments/assets/efa51b33-f283-4a95-ad86-704e401e6e31)




Terraform Fig 9

Run terraform init and terraform apply:

![Terraform Fig11a](https://github.com/user-attachments/assets/4e0b209e-4da0-4e26-b350-78baf8b2b1f0)



Machines installation completed

![Terraform Fig12](https://github.com/user-attachments/assets/eb31fcf4-a2d5-49d8-b5d7-9de0a9bc1aaa)


![Terraform Fig12](https://github.com/user-attachments/assets/33a9c69a-4b3d-447f-89d8-d546d3111560)


Terraform Setup: Install and configure Terraform for AWS by setting up AWS CLI and access credentials.

Workstation Configurations: For Bue Team, Red Team and Victim Workstation

Blue Team HELK machine:  this machine is also Amazon Linux 2 with size t2.large (8 GB, 2 vcpu) and 30 GB of disk space. HELK integrates multiple technologies, making it versatile for cybersecurity operations such as ELK Stack, Elasticsearch, Logstash, Kibana, Apache Kafka, Spark, Jupyter Notebooks.

Red Team Caldera machine:  This machine is Amazon Linux 2 (Redhat based) with size t2.micro (no cost with AWS Free tier). 
