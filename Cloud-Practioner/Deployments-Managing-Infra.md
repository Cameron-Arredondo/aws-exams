# Deployments & Managing Infrastructure at Scale

## CloudFormation
CloudFormation is a declarative way of outlining your AWS infrastructure for any resources (Infrastructure as Code).  You can estimate the costs of your infrastructure using cloudformation.  There is even a CloudFormation Stack Designer available
## CDK Cloud Development Kit
Build you infrastructure using Python!! The code you write will then be compiled into a cloudformation template and deploy the infrastructure and runtime code together!
- Great for Lambda Functions, Docker Containers (ECS/EKS)
## Beanstalk
Typical Architecture: Web App 3-tier
- ELB -> EC2 instances in ASG -> Read/Write data to DB (AWS RDS)

Elastic Beanstalk is developer centric view of deploying apps to AWS. Beanstalk would be considered as a PaaS = Platform as a Service.
- Managed Service
- Load balancing, Application Health Monitoring done by beanstalk
- Devs are responsible for the application code.
#### Three Architecture Models:
- Single Instance
- LB + ASG
- ASG only
#### Two Environment Tiers:
Web Server Environment and Worker Environment

## Code Deploy
Works with EC2 instances and on prem services.  Code deploy allows us to upgrade EC2 applications and on premises applications.
## Code Commit
VCS for AWS that is for git based repos.  Code lives within AWS account and is private to AWS
## Code Build
code, test and deploy packages in AWS.  It is Fully managed and serverless.  BUILD CODE & RUN TESTS
## Code Pipeline
CI/CD for AWS which allows you to have different steps for your code: Build, Test, Deploy, Post Deploy. Compatible with Code Commit, Code Deploy, Code Build, CloudFormation, Github.
## Code Artifact
Code Artifact is a secure, scalable and cost-effective artifact management service (package management, think pip, npm, yarn and etc).  It is place to store and retrieve the packages.  
## CodeStar
Unified UI to easily manage software development activities (all the code related services in AWS) in one place.
## Cloud9
Is a Cloud IDE (think VSCODE, IntelliJ)
## AWS SSM (Systems Manager)
Helps manage EC2 instances at scale (patching automatically).
To use SSM you need to install the SSM agent on to the instance.
## AWS SSM (Session Manager)
Allows you to start a secure shell in your EC2 instance on to the servers.  Allows you to not require SSH keys and have port 22 open.
## AWS OpsWorks
is an AWS managed Chef & Puppet instance in the cloud.  You can only provision standard AWS resources.  OpWorks have a stack which contains layers that define ALB, EC2 and RDS in each layer