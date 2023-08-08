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

#### S3 Bucket Polices:
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
### S3 Websites - Static Website Hosting
- Enable Static Website hosting and hosting type would be bucket hosting
- Bucket must have policy that allows public reads.  This is where you could upload HTML files to the bucket and have it be a static website. 

### Versioning files
- You can enable versioning at the bucket level which will allow you to have several different versions. This allows you to roll back easy and also protect against unintended deletes.
- Any file that is not versioned prior to enabling versional will have the version "null"
- suspending versioning does not delete the previous versions
