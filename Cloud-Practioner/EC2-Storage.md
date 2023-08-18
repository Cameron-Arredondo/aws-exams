# EC2 Storage Notes

- AMI = Amazon Machine Image
Public AMIs = AWS provided AMIs
Personal AMIs = You create your own AMI
Marketplace AMIs = Vendors

- UserData on an instance allows you to run a start up script for that respective image.

- EBS = Elastic Block Store, this is a network drive that can be attached to instances while they run, this allows us to persist data.

- EBS at the CCP level can only be mounted to one instance at a time.  In higher levels of AWS courses there is a multi-attach feature that for some EBS (IOPS).  

- EBS volumes are bound to a specific availability zone

- EBS volumes use the network to communicate to the instance which means there could be some latency.  Volumes can be detached from one instance and attached to another one pretty easily so that data can be transferred.

- EBS volumes do not always need to be attached and the can be attached on-demand usage.

- EBS delete on termination attribute, when we create an EBS volume.  By default the root EBS volume attached to an instance is deleted on termination of the instance.  This can be enabled or disabled to control whether the EBS would be deleted or not.

- EBS volumes have a provisioned capacity so this means that you will get billed based on how much you are provisioned.

- EBS snapshots, this allows you to back up your EBS volume at a point in time.  It is recommended to detach your volume to do a snapshot but not always necessary.

- Snapshots can be copied across different AZ/Regions which would provide a way to transfer data to an instance in another availability zone.

- EBS features:
EBS Snapshot Archive = Snapshots can be moved to archive to make it 75% cheaper but it will take 24 to 72 hours to restore. 
EBS recycle bin = will have all the snapshots that are deleted, you can specify retention on the recycle bin.

- EC2 Image Builder:
Used to automate creation of VMs or container images.  There is an EC2 Image builder service that will create an ec2 instance publish an AMI for it and then perform an automated test instance from the AMI and distribute that instance to  multiple different regions.

- EC2 Instance Store: EBS volumes are network drives with good but limited performance.  EC2 instance store is a high performance hardware disk with better I/O performance.  EC2 instances are ephemeral so this is not a good option for keeping state of data.  This is good for temporary data.  

- EFS = Elastic File System, this is a network files system that can be mounted on hundreds of EC2 instances at a time.  Shared Network Filesystem (NFS).  EFS only works with Linux EC2 instances and works across multiple availability zones.  EFS is Highly Available but can be expensive, it is three times the cost of an gp2 EBS volume.  EFS is a pay per use cost method.  EFS can be attached to a security group. 

- EBS vs EFS
EBS can only be attached to one instance in one specific AZ, EBS volumes are bound to a specific AZ.  Snapshots will allow you to move EBS volumes over but it is a copy.  EFS is a network filesystem which allows the drive to be shared to everything that is mounted to it. Instances in the different AZ can be mounted to an a single EFS.

- EFS Infrequent Access (EFS-IA) Storage class that is cost-optimized for files not accessed every day.  Up to 92% lower cost compared to EFS.  EFS will automatically moves your files to EFS-IA based on the last time they were accessed.  EFS-IA can be enabled with a lifecycle policy which can specify that if a file hasn't been touched for 60 days, move it to EFS-IA.  This is transparent to applications accessing EFS 

- Shared Responsibility Model for EC2 storage

    - AWS: Infrastructure, Replication for data for EBS volumes and EFS drives, replacing faulty hardware, their employees cannot access data

    -  AWS-User: Data back, snapshot.  Data encryption and responsibility of data on drives.  Understanding risk of use EC2 Instance Store.
- AWS FSx
    - Fully Managed Service
    - FSx for Windows File Server is a fully managed, highly reliable, and scalable Windows native shared file system.  It's built on Windows File Server and supports SMB protocol & Windows NTFS.  Integration for AD is available.  Can be access from AWS or your on-premise infrastructure
    - FSx for Lustre is for High Performance Computing.  It is for linux clusters which is built for ML, video processing, financial modeling.  Has great IOPS 