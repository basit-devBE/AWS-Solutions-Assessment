# AWS Multi-Tier Architecture Example

This diagram illustrates a highly available, secure, and scalable AWS multi-tier architecture. It demonstrates how to deploy a web application using best practices for networking, security, and redundancy across multiple Availability Zones (AZs).

## Architecture Overview
- **Route 53**: Provides DNS routing for incoming browser requests.
- **Application Load Balancer (ALB)**: Distributes traffic across frontend instances in multiple AZs.
- **Auto Scaling Groups**: Automatically scale frontend and backend EC2 instances based on demand.
- **Public and Private Subnets**: Separate resources for security and accessibility. Public subnets host frontend instances; private subnets host backend and database resources.
- **NAT Gateways**: Allow instances in private subnets to access the internet securely.
- **Amazon RDS (Multi-AZ Deployment)**: Provides a highly available, fault-tolerant relational database with automatic failover.
- **AWS CloudFormation**: Automates the deployment and management of AWS resources.

## Security Groups
- **ALB Security Group**: Allows inbound HTTP (80) and HTTPS (443) traffic from anywhere.
- **Frontend Security Group**: Allows inbound traffic on port 80 from the ALB only.
- **Backend Security Group**: Allows inbound traffic on port 8050 from the frontend only.
- **RDS Security Group**: Allows inbound traffic on port 3306 from backend instances only.
- **CloudFormation Security Group**: Allows inbound traffic from NAT Gateway for provisioning.

## Key Features
- **High Availability**: Resources are distributed across two Availability Zones for redundancy.
- **Scalability**: Auto Scaling Groups ensure the application can handle varying loads.
- **Security**: Layered security using security groups and subnet isolation.
- **Automation**: Infrastructure is managed and provisioned using AWS CloudFormation.

## Usage
This architecture is suitable for:
- Web applications requiring high availability and scalability
- Environments needing strong security and network isolation
- Automated, repeatable infrastructure deployments

---

*For more details, refer to the architecture diagram above and the associated security group rules.*
