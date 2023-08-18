# AWS Networking
## VPC
VPC stands for virtual private cloud
## IP Addresses in AWS
- IPV4
    - Public IPV4 can be used on the internet, EC2 instances gets a new public IP every time you stop and then start it
    - Private IPV4 can be used on private networks (LAN) such as internal AWS networking.  These Private IPV4 addresses are constant

Elastic IP: Allows you to attach a fixed public IPV4 address to an EC2 instance

- IPV6 is Internet Protocol version 6 
    - Every IP address is public (no private range)

## VPC and Subnets
- VPC is a private network to deploy your AWS resources.
- Subnets allow you to partition your network inside your VPC
- A public subnet is a subnet that is accessible from the internet
- A Private subnet is not accessible from the internet
- Route Tables allow us to define access to the internet and between subnets.

VPC CIDR Range = List of IP addresses allowed within a VPC
## Internet Gateway & NAT Gateways
- Internet Gateways help our VPC instances connect with the internet
- Public Subnets have a route to the internet gateway
- NAT Gateway will allow instances in private subnet to access the internet while remaining private.

- There are several subnets available within the default VPC, all a subnet is doing is segment our network inside the VPC.
- See some details of the CIDR with CIDR.xyz
- Internet Gateway will be attached to a VPC, a VPC can only have 1 Internet Gateway
-  Subnets will have their own route tables that define what local and public access the subnet will have
- NAT Gateway will be associated with a subnet and will allow the instances in a private subnet to access the internet.