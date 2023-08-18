# Leveraging AWS Global Infrastructure
## Why Deploy Globally
A global application is an application deployed in multiple geographies.  On AWS this would be Regions, deploying to multiple geographies will decrease latency for users across the world.  Having apps in different region helps when it comes to Disaster Recovery and could help in the case of a Cyber Attack. 
- [AWS INFRASTRUCTURE](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)
## AWS Route 53
- Managed DNS
- DNS is a collection of rules and records which helps clients understand how to reach a server through URLs.

![Records in AWS](images/AWS-DNS-Records.png)
## Routing Policies
- Simple Routing policy (no health checks)
- Weighted Routing Policy (distribute traffic across routes, will use health checks)
- Latency Routing Policy, will look at where the user is located and utilize the server that is nearest to them.  This minimizes latency
- Failover Routing Policy, Primary instance and Failover. Route53 will determine where to route traffic to based on the health check of the instances.  This is good for disaster recovery.
## AWS Cloudfront
Cloudfront is Content Delivery Network (CDN)
- Cloudfront improves read performance, content is cached at the edge
- 216 Point of Presence globally (edge location)
- DDOS protections, integration with Shield, AWS WAF
## Cloudfront Origins
- S3 bucket can be used to distribute files and cache them at the edge, this comes with enhanced security with Cloudfront Origin Access Control (OAC).  OAC is replacing Origin Access Identity (OIA).  Cloudfront can also be used as an ingress to upload files to S3
- Custom Origin (HTTP)
    - Application Load Balancer
    - EC2 instance
    - S3 Website (must first enable the bucket as a static S3 site)
    - Any HTTP backend we want to use

## Cloudfront walk through
- Put html file in bucket
- Go to Cloudfront, determine origin domain, then you will set origin access (public, private, Origin Access Control)
- Create OAC
- Policy will need to be applied to the specific S3 bucket to allow Cloudfront service to get object on the S3 bucket
- Origin Access Controls will be assigned to a certain distribution
## S3 Transfer Acceleration
- Transfer speed can be increased by transferring file to an AWS edge location which will forward the data to the S3 bucket in the target region
- This is used when we want to upload file to an S3 bucket that is far from us.  
## AWS Global Accelerator
Users will connect to an edge location and leverage private AWS connection to access the LB -> EC2.  
- 2 Anycast IPs are created
### cloudfront vs Global Accelerator
- Cloudfront is a Content Delivery Network which caches content at the edge to improve performance
- Global Accelerator there is no caching, all requests are passed from edge locations to apps in whatever region.  Good for HTTP requests.
## AWS Outposts
Hybrid Cloud: Have on premise infrastructure along with cloud infrastructure.  AWS outposts are server racks that AWS will set up and manage within your on-premise infrastructure, outpost will have AWS API's, tools and etc to build application similar to how you would in the cloud.
You would be responsible for physical security of AWS outpost server rack.
## AWS WaveLength
- Will allow you deploy some AWS services to the edge of 5G networks.  
- Will provide ultra low latency, traffic will also not leave the Communication Service Provider.
Use Case: Smart Cities
## AWS Local Zones
Allows you to place compute closer to end users.  You will extend your VPC to more locations "Extension of an AWS Region". 

Example:
- AWS Region (us-east-1)
- AWS local zones can reach out to Dallas, Chicago and etc.  
# Global Application Architectures
Single Region Single AZ Architecture:
- Does not provide high availability
- Does not provide Global Latency
- It is easy to set up

Single Region, Multi AZ:
- Achieves high availability 
- Does not provide global latency
- slight difficult

Multi-Region, Active-Passive:
- Two regions where each region will have one or multiple AZ's
- Active region will do read and writes
- Passive region will do only reads
- improves latency
- latency for writes are still going to have latency.

Multi-Region, Active-Active:
- Latency for read and writes is improved (is quick)
- It is difficult to set up
- Two regions, each region will have one or multiple AZ's with active notes (Read & write)

