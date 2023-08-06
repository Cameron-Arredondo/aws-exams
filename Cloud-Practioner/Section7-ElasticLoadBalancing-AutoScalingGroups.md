# Elastic Load Balancing and Auto Scaling Notes

## Vertical Scaling 
- Scale the size of the resource being used (t.2 micro - t.2 large).  The concept is to add more power of a resource.

## Horizontal Scaling
- Scale the number of nodes that are being used.  This can be thought of as hiring more people instead of hiring a single senior employee.

# Load Balancing
- Spreads load across multiple downstream instances.  This will be placed in front of servers and distribute the load based on an algorithm
-  Expose a single point of entry (DNS) to your app.
- perform regular health checks to downstream instances and seamlessly handle failures on downstream instances.
- Provide SSL termination (HTTPS) for websites.
- ELB is Elastic Load Balancer.  ELB is a managed load balancer. AWS takes care of maintenance, availability, and guarantees it will be working.  The user would only need to set up a few configurations.
### Types of Load Balancers
- Application Load Balancer (Layer 7)
- Network Load Balancer (Layer 4)
- Gateway Load Balancer (Layer 3)
###  Application Load Balancer
- focused on HTTP/HTTPS and gRPC
- HTTP Routing features
- Static DNS (URL)
### Network Load Balancer 
- TCP/UDP protocols (layer 4)
- High Performance: millions of requests per second
- Static IP through Elastic IP
### Gateway Load Balancer
- GENEVE Protocol on IP packets (Layer 3)
- Route traffic to firewalls that you manage on EC2 instances.  This allows you to perform Intrusion Detection, Deep packet inspection and classic firewall.  The Gateway balances the load to the virtual appliances that run on ec2 instances so that traffic can be analyzed and or perform firewall operations. The traffic is then sent back to the Gateway Load Balancer and then forwarded back to the application.
### Hands On Load Balancing
When setting up load balancing for servers in the cloud you need to create a target group.  The Load Balancer will then send traffic to any of those nodes in the group.

Load Balancing can be seen and set in the EC2 services section of the AWS. 

# Auto Scaling
In the cloud it is easy to create and get rid of servers quickly.

The goal of an Auto Scaling group is:
 - Scale out, add EC2 instances to to match an increased load
 - Scale in, remove EC@ instances to match a decreased load
 - ensure we have a minimum and a maximum number of machines running
 - automatically register new instances to a load balancer
 - replace unhealthy instances
 - cost savings: allows us to run optimally

You can set maximum and minimum sizes for scaling purposes.  

Auto Scaling Strategies:

- Manual Scaling: update the size of our autoscaling group manually

Dynamic Scaling: Response to changing demand (Simple/Step Scaling, Target Tracking Scaling, Scheduled Scaling), and Predictive Scaling.