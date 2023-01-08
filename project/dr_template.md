# Infrastructure

## AWS Zones
Identify your zones here

us-east-1 region availibility zones : ["us-east-2a","us-east-2b", "us-east-2c"]
us-west-1 region availibility zones : ["us-west-1a", "us-west-1b"]


## Servers and Clusters

### Table 1.1 Summary
| Asset      | Purpose           | Size                                                                   | Qty                                                             | DR                                                                                                           |
|------------|-------------------|------------------------------------------------------------------------|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EC2 Instances | For Ubuntu VMs | t3.micro | 3 per region | Multiple regions/availibilty zones |
| EKS | Monitoring | t3.medium | 1 cluster (2 nodes minimum) per region | created in multiple locations |
| VPC | Virtual Private Cloud | N/A | 1 per region | created in multiple locations |
| RDS | database | db.t2.small | 1 cluster (3 instances) per region | Clusters replicated between zones 1 and 2 |
| Key Pairs | For accessing EC2 instances | N/A | 1 per region | Created in multiple regions |
| Internet Gateway | public subnets | N/A | 1 per region | Created in multiple regions |
| Private Subnet | not accessible directly from internet | N/A | 1 per availability zone in each region | Created in multiple regions |
| Public Subnet | accessible directly from internet | N/A | 1 per availability zone in each region | Created in multiple regions |
| NAT Gateway | Network Address Translation | N/A | 1 per availability zone in each region | Created in multiple regions |
| EIP | Elastic IP Address | N/A | 1 per availability zone in each region | Created in multiple regions |
| ALB | Application Load Balancer | N/A | 1 per region | Created in multiple regions |

### Descriptions
More detailed descriptions of each asset identified above.

To host applications we use EC2 instances as web servers.
Communication between VPC and the Internet is made possible by the Internet Gateway.
Private Subnet is a logical subnet; it prevents access to/from the Internet directly.
Key pairs are used to access the EC2 instances.
A logical subnet called Public Subnet allows access to and from the Internet through an Internet Gateway.
Network address translation service is what NAT Gateway is.
The public address of the NAT Gateway is represented by an elastic IP address (static IPv4 address).
Requests are uniformly distributed among EC2 machines by the the load balancer.
Database services include RDS Cluster.
Virtual Private Cloud, or VPC, is a private cloud that is safe and separated within a larger AWS area.

## DR Plan
### Pre-Steps:
List steps you would perform to setup the infrastructure in the other region. It doesn't have to be super detailed, but high-level should suffice.

Create a unique S3 bucket in a new region and copy the AMI image.
Create a key-pair with the name udacity in the region
Make changes to the .tf files for the zones to define the config for files such as config, load_balancer, modules.
Deploy the entire stack as same using terraform apply
Resolve any errors related to mintoring namespace or IAM issue using the workarounds

## Steps:
You won't actually perform these steps, but write out what you would do to "fail-over" your application and database cluster to the other region. Think about all the pieces that were setup and how you would use those in the other region

Change the DNS to Zone2 LB
Stop RDS in zone1 -> it will make RDS of zone2 as primary and failover
