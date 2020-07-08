---
description: Virtual Private Cloud
---

# AWS VPC

## About VPC

Virtual Private Cloud is the location where servers are launched.

1. VPC can be viewed as a house for servers
2. VPC can be partitioned into **subnets**
3. Each subnet can communicate with each other provided by routes
4. To communicate globally, a subnet must have route linked to `0.0.0.0/0` 
5.  Each EC2 instance is created under a VPC within a specific subnet; hence, the instance will be protected \(or not be protected\) under the configuration of the VPC



