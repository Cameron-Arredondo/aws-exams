# AWS Other Services
## Amazon Workspaces
- Amazon Workspaces is a managed Desktop as a Service (DaaS) solution to easily provision Windows or Linux desktops.
- Great to eliminate management of on-premise VDI (virtual desktop infrastructure)
- Fast and scalable
- Secured data - integrates with KMS
- Pay as you go 
- Best practice is to deploy workspace as close to user as possible
## Amazon AppStream 2.0 
- Desktop Application Streaming Service
- Stream specific Desktop Application into your web browser
- works with any device that has a web browser
- allowed to configure an instance type per application (CPU, GPU, RAM)
## AWS IoT Core
- Allows you to easily connect IoT devices into the cloud
- Allows devices to communicate even when they are not connected
- Integrates with a lot of AWS services
- gather, process and analyze and act on data
## AWS elastic transcoder
- coverts media files stored in S3 into media files in the formats required by consumer playback devices (phones etc...)
- Input S3 bucket -> run through transcoding pipeline -> Output to S3 bucket -> Consumable by Smartphones, Tablets, PCs and etc.

Pros:
- Easy to use
- Highly Scalable - can handle large volumes of media files and large file sizes
- Cost effective, aws fully managed and secure

## AWS AppSync
- Store and sync data across mobile and web apps in real-time using GraphQL
- In the test if you see GraphQL it will hint heavily for you to use AppSync
- Integrations with DynamoDB / Lambda
- Real-time subscriptions
- Offline data synchronizations (replaces cognito sync)
- Fine Grained Security
- AWS amplify can leverage AWS  AppSync in the background
## AWS Amplify
- Is a set of tools and services that helps you develop and deploy scalable full stack web and movie applications
## AWS Device Farm 
- Fully managed service that tests your web and mobile apps against desktop browsers, real mobile devices and tablets
- Run tests concurrently on multiple devices (speed up execution)
- Ability to configure device settings (GPS, language, Wi-Fi, Bluetooth)
- Device Farm will send logs back to user
## AWS backup
- Fully managed service to automate and manage back ups across AWS services
- Create back up plan and then assign resources to the back up plan and will be stored in AWS S3
## Disaster Recovery Strategies
![DR](images/DR-backup-restore-pilot-light.png)
![DR](images/DR-Warm-standby-hot-site.png)
- Multi-Region setup can failover from us-east-1 to eu-west-2 in the instance of a regional failure
## AWS Elastic Disaster Recovery
- Allows you to quickly and easily recover your physical, virtual, and cloud-based servers into AWS
- Performs Continuous block-level replication for your servers

![AWS EDR](images/AWS-EDR.png)
## AWS DataSync
- Move large amount of data from on-premises to AWS
- Can synchronize to: Amazon S3 (any storage class), Amazon EFS, Amazon FSx for Windows
- Replications tasks can be scheduled hourly, daily and weekly
- replication tasks are incremental after the first full load 
## AWS Application Discovery Service
- Plan migration projects by gathering information about on-prem data centers
- dependency mapping for migrations
### Agentless Discovery (AWS Agentless Discovery Connector)
- VM inventory, configuration, and performance history such as CPU, memory and disk usage
### Agent-based Discovery (AWS Application Discovery Agent)
- System configuration, system performance, running processes, and details of the network connections between systems

This data can be aggregated and view in AWS Migration Hub

## AWS Application Migration Service
- Converts your physical, virtual and cloud based servers to run natively on AWS
- You need to install replication agent at data-center
- supports wide range of platforms, Operating Systems, and databases
- Minimal downtime, reduced costs

## AWS Migration Evaluator
- Helps you build a data-driven business case for migration to AWS
- Provides a clear baseline of what your org is running today
- Install Agentless Collector to conduct broad-based discovery
- Take a snapshot of on-premises foot-print, server dependencies
- analyze current state, define target state, then develop migration plan
- This can be done by installing collector or importing data to the AWS Migration Evaluator
## AWS Fault Injection Simulator (FIS)
- A fully managed service for running fault injection experiments on AWS workloads
- Based on Chaos Engineering - stressing an application by creating disruptive events
- Helps you uncover hidden bugs and performance bottlenecks
- Supports EC2, ECS, EKS, RDS
- Lets you choose from pre-built templates that generate the desired disruptions
## Step Functions
- Build serverless visual workflow to orchestrate your lambda functions
- Features: sequence, parallel, conditions, timeouts, error handling
- Can integrate with EC2, ECS, SQS queues etc...
- Possibility of implementing human approval feature
## AWS Ground Station
- Fully managed service that lets you control satellite communications, process data, and scale your satellite operations
- Allows you to download satellite data to your AWS VPC within seconds
- Use Cases: Weather Forecasting, surface imaging, communications, video broadcasts
## Pinpoint
- Scalable 2-way marketing communications service
- Supports email, SMS, push, voice and in app messaging
- Ability to segment and personalize messages with the right content to customers
- possibility to receive replies
- Scales to billions of messages per day
- Use cases: run campaigns by sending marketing, bulk, transactional SMS message
- Versus Amazon SNS or Amazon SES
    - in SNS & SES you managed each message's audience, content, and delivery schedule
    - in Amazon pinpoint you create message templates, delivery schedules, highly-targeted segments, and full campaigns
    
