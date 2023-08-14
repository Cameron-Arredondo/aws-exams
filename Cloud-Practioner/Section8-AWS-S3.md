# AWS S3
Infinitely scaling storage

## Use Cases
- Back up/ Storage
- Disaster Recovery
- Archive Files
- Hybrid Cloud Storage
- Application hosting
- Host Media
- Data Lake and Big Data Analytics
- Host static websites

Amazon S3 allows people to store files in buckets (directories)
Buckets Must have a globally unique name (across all regions)
Buckets are defined at the region level
no uppercase, no underscore for naming buckets

## Objects
Objects are (files) have a key.  The key is the Full Path, the key is composed of a prefix + object name.
- Object values are the content of the body:
    - Max OBJ size is 5TB (5000GB)
    - If uploading more than 5GB, must use "multi-part upload"
    - Metadata, Tags, Version ID
- Objects can be accessible via the public URL. 
- PresignedURL is intended only for the person who created the object in the bucket.
- buckets can have folders with objects in them
## Security
- User-based
    - IAM Policies - which API calls should be allowed for a specific user from IAM 

- Resource-based
    - Bucket policies- bucket wide rules, allows cross account
    - Object Access Control List (ACL) - finer grain (can be disabled)
    - Bucket Access Control List (ACL) - less common (can be disabled)

- Encryption: encrypt objects in Amazon S3 using encryption keys

## S3 Bucket Polices:
- JSON based policies which specify things like GetObject for a specific resource
- Effect will allow or deny the action specified in the JSON.  
- Principal represents the account or user to apply the policy to.
- We use these policies to grant access, force object to be encrypted at upload and grant access to another account.
- EC2 instance we to give access to an S3 bucket, we need to use IAM roles.  We would apply EC2 instance role to the instance and attach the proper IAM permissions.

- Cross Account Access
    - Use bucket policy that allows cross account access for the specific IAM user. Then the User in the other AWS account will be able to make API calls to the S3 bucket.
### Note
- An IAM principal can access an S3 object if:
    - The user IAM permissions ALLOW (ROLE) it OR the resource policy(policy attached to S3) ALLOWS it AND there's no explicit DENY
## S3 Websites - Static Website Hosting
- Enable Static Website hosting and hosting type would be bucket hosting
- Bucket must have policy that allows public reads.  This is where you could upload HTML files to the bucket and have it be a static website. 

## Versioning files
- You can enable versioning at the bucket level which will allow you to have several different versions. This allows you to roll back easy and also protect against unintended deletes.
- Any file that is not versioned prior to enabling versional will have the version "null"
- suspending versioning does not delete the previous versions

## S3 Replication
To utilize replication Versioning in source and destination buckets must be enabled!  Copying is asynchronous.

- CRR: Cross Region replication
- SSR: Same Region Replication

You will need to create an IAM role when doing the replication.
When files are replicated it will have the same version ID as the item in the original bucket.

## Storage Classes
Durability: Will hardly ever lose data!
Availability: How readily the service is! 99.99% availability for the year.

- S3 standard: 99.99% availability, can be used for frequently accessed data and has low latency and high throughput

- Infrequent Access: Lower cost than standard S3, this for data that is less frequently access.  Use Case: Disaster Recovery, backups

- Glacier Storage Class: Low-cost object storage meant for archiving/backup
Glacier Instant Retrieval: can be access in milliseconds and has a minimum storage duration of 90 days
Flexible Retrieval: Expedited (1-5 mins), Standard(3-5 hours), Bulk(5-12 hours).  Minimum store duration is 90 days.

Deep Archive: Standard(12 hours), Bulk(48 hours) 
S3 Intelligent Tiering:  Allows you to move object between access tiers based on usage.  There are no retrieval charges.

## Encryption
- Server-Side Encryption (Default).  Server performs encryption after receiving file.
- Client Side Encryption, the user will encrypt the file before uploading it to S3.
## Shared Responsibility Model
- AWS responsible for all infrastructure (security, availability).
- User is responsible for S3 versioning, S3 Bucket Policies, S3 Replication, Logging and Monitoring, S3 Storage Class, Data encryption at rest and in transit

## AWS Snow Family
- Data Migration (Snowcone, Snowball Edge, Snowmobile)
- Edge Computing (Snowcone, Snowball Edge)
### Data Migration
if it takes more than a week to transfer over the network, use snowball devices!
The Snow Family are offline devices that allow you to perform data migrations.

- AWS will ship Snowball device to you, you upload the data send it back and then AWS will upload to their infrastructure directly (Amazon S3).
- Snowball Edge is used to move TBs or PBs of data in or out of AWS, it's an alternative to moving data over the network. 
- Snowcones are rugged and secure and meant for environments with a little bit of data. (must provide own battery and cables for device).
- Snowmobile can transfer exabytes of data 1,000 PB or 1,000,000 TB of data. It is a huge truck that has video surveillance.  

### Edge Computing
Process data while it's being created on an edge location.  Edge location could be truck on the road or a ship for example.  Edge locations will have limited internet access or no access at all.  Snowball Edge and snowcones can perform Edge Computing.

Use of edge computing:
- Preprocess Data
- Machine learning at the edge
- Transcoding media streams

The Snowball Edge compute optimized. storage optimized and Snowcone can run EC2 instances, AWS lambda functions using AWS IoT Greengrass.
### AWS OpsHub
OpsHub is software install on machine and will provide a GUI to manage your Snow Family Device, launce AWS services and create Network Storage
## Storage Gateway
Hybrid Cloud Storage, Bridges on premise data and cloud data in S3.
It is a way to bridge filesystem and storage on premise into the cloud to leverage the best of both worlds.

Types of Storage Gateways:
- File Gateway (ex: NFS)
- Volume Gateway (Block ex: EBS)
- Tape Gateway