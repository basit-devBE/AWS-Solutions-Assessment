# AWS Well-Architected & Cloud Adoption Framework Assessment

## Project: Two-Tier Web Application Migration to AWS

---

## Task 2 – AWS Well-Architected Framework (WAF) Assessment

| Pillar | Observation | Improvement | Recommendation | Supporting AWS Service |
|------|-----------|------------|---------------|------------------------|
| Operational Excellence | Deployment is manual and not repeatable. | Automate infrastructure provisioning and deployments. | Use Infrastructure as Code and CI/CD pipelines. | AWS CloudFormation, CodePipeline, CodeBuild |
| Security | Network access is loosely defined and could expose resources. | Enforce least-privilege and layered security. | Implement security groups per tier and restrict traffic flow. | Security Groups, IAM, AWS Shield, AWS WAF |
| Reliability | Single database instance is a single point of failure. | Improve fault tolerance and availability. | Use Multi-AZ architecture and Auto Scaling across AZs. | Amazon RDS Multi-AZ, Auto Scaling, Elastic Load Balancer |
| Performance Efficiency | Fixed instance sizes limit scalability. | Enable dynamic scaling and performance optimization. | Use Auto Scaling and managed load balancing. | Auto Scaling Groups, Application Load Balancer |
| Cost Optimization | Always-on resources increase costs. | Optimize resource usage and reduce waste. | Scale on demand and monitor spending. | AWS Cost Explorer, Auto Scaling, AWS Budgets |

---

## Task 3 – Cloud Adoption Framework (CAF) Readiness Summary

### 1. Business Perspective
The organization shows strong motivation to migrate its two-tier application to AWS to improve scalability and reliability. However, there is limited clarity on business KPIs and success metrics. To ensure alignment, the organization should define measurable outcomes such as availability targets, deployment frequency, and cost optimization goals. AWS services such as AWS Migration Hub and AWS Well-Architected Tool can help align business objectives with technical outcomes and track progress throughout the migration journey.

### 2. People Perspective
The team has basic AWS knowledge but lacks advanced cloud and DevOps skills. Training and enablement are required to ensure engineers can design, deploy, and operate cloud workloads effectively. The organization should invest in structured learning paths, certifications, and hands-on labs. AWS Skill Builder and AWS Training and Certification will help upskill staff and build cloud fluency across teams.

### 3. Governance Perspective
Currently, there is limited governance around security, compliance, and cost control. This presents a risk as the cloud environment grows. The organization should establish policies for account structure, tagging, cost management, and security baselines. AWS Organizations, Service Control Policies (SCPs), and AWS Config will help enforce governance and maintain compliance at scale.

### 4. Platform Perspective
The existing on-prem architecture is not designed for elasticity or high availability. The platform should be redesigned to use AWS native services such as VPC, Application Load Balancer, Auto Scaling Groups, and Amazon RDS Multi-AZ. Infrastructure as Code should be adopted to ensure consistency and repeatability. AWS CloudFormation will enable automated and standardized environment provisioning.

### 5. Security Perspective
Security is currently perimeter-based and not aligned with a zero-trust model. The cloud design must enforce least privilege, network segmentation, encryption, and monitoring. The organization should implement IAM roles, security groups, AWS WAF, and AWS Shield for protection, along with AWS CloudTrail and GuardDuty for auditing and threat detection.

### 6. Operations Perspective
Operational processes are manual and reactive, leading to slow incident response and inconsistent deployments. The organization should implement monitoring, logging, and automation to improve operational maturity. Amazon CloudWatch, AWS Systems Manager, and AWS Config will enable proactive monitoring, patching, and operational excellence.

---

## Task 4 – Improved Architecture Design (Aligned with WAF & CAF)

### Architecture Description

The improved architecture uses a highly available, secure, and scalable two-tier design deployed across two Availability Zones within a single VPC.

**Traffic Flow:**
Browser → Amazon Route 53 → Application Load Balancer → Frontend Auto Scaling Group → Backend Auto Scaling Group → Amazon RDS Multi-AZ

**Key Components:**

- **VPC** with public and private subnets across two Availability Zones
- **Internet Gateway** for public access and **NAT Gateways** for private subnet outbound access
- **Application Load Balancer** in public subnets
- **Frontend Auto Scaling Group** in public subnets
- **Backend Auto Scaling Group** in private subnets
- **Amazon RDS Multi-AZ** in private subnets for high availability
- **Security Groups** enforcing least-privilege between tiers
- **CloudFormation** for Infrastructure as Code
- **CloudWatch & CloudTrail** for monitoring and auditing
- **AWS WAF & Shield** for edge protection

This design improves security, reliability, scalability, and operational efficiency while aligning with AWS best practices.

---

## Reflection 

This lab helped me understand how cloud architecture is more than just placing services together; it requires structured evaluation using proven frameworks. By applying the AWS Well-Architected Framework, I learned how each pillar directly influences design decisions such as using Auto Scaling for performance and RDS Multi-AZ for reliability. The Cloud Adoption Framework showed that successful migration is not only technical but also organizational, requiring governance, training, and operational maturity. Redesigning the two-tier architecture reinforced the importance of network segmentation, least-privilege security, and automation using Infrastructure as Code. Overall, this exercise strengthened my ability to think like a cloud architect by evaluating workloads holistically and designing solutions that are secure, scalable, and aligned with business objectives.

---