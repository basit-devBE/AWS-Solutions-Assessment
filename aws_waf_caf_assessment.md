# AWS Well-Architected & Cloud Adoption Framework Review

## Project: Migrating a Two-Tier Web Application to AWS

---

## Task 2 – AWS Well-Architected Framework (WAF) Evaluation

| Pillar | Current State | Enhancement | Guidance | Relevant AWS Services |
|--------|--------------|-------------|---------|----------------------|
| Operational Excellence | Deployments are performed manually and lack consistency. | Introduce automation for infrastructure setup and application delivery. | Adopt Infrastructure as Code and continuous integration/deployment workflows. | AWS CloudFormation, CodePipeline, CodeBuild |
| Security | Network permissions are broad, risking exposure of resources. | Strengthen security by applying least privilege and layered controls. | Define security groups for each layer and restrict inter-tier communication. | Security Groups, IAM, AWS Shield, AWS WAF |
| Reliability | The database is a single point of failure. | Increase resilience and availability. | Implement Multi-AZ deployments and auto scaling across zones. | Amazon RDS Multi-AZ, Auto Scaling, Elastic Load Balancer |
| Performance Efficiency | Static instance sizes hinder scalability. | Enable flexible scaling and optimize performance. | Utilize Auto Scaling and managed load balancing solutions. | Auto Scaling Groups, Application Load Balancer |
| Cost Optimization | Resources run continuously, leading to higher costs. | Improve cost efficiency and reduce unnecessary spend. | Scale resources based on demand and monitor usage. | AWS Cost Explorer, Auto Scaling, AWS Budgets |

---

## Task 3 – Cloud Adoption Framework (CAF) Readiness Overview

### 1. Business Perspective
The company is motivated to transition its two-tier application to AWS for enhanced scalability and reliability. However, business KPIs and success criteria are not well defined. To ensure objectives are met, measurable goals like uptime, deployment speed, and cost savings should be established. AWS Migration Hub and the Well-Architected Tool can help align business goals with technical deliverables and monitor progress during migration.

### 2. People Perspective
The technical team possesses foundational AWS skills but needs further expertise in cloud and DevOps practices. Upskilling is necessary to empower engineers to architect, deploy, and manage cloud solutions. Investment in training, certifications, and practical labs is recommended. AWS Skill Builder and AWS Training and Certification can support workforce development and cloud proficiency.

### 3. Governance Perspective
Governance for security, compliance, and cost management is currently minimal, which could become problematic as cloud usage expands. The organization should implement policies for account management, resource tagging, cost tracking, and security standards. AWS Organizations, Service Control Policies, and AWS Config can help enforce governance and maintain compliance.

### 4. Platform Perspective
The current on-premises setup lacks flexibility and high availability. The platform should be re-architected to leverage AWS-native services like VPC, Application Load Balancer, Auto Scaling Groups, and Amazon RDS Multi-AZ. Adopting Infrastructure as Code will ensure consistent and repeatable deployments. AWS CloudFormation can automate and standardize environment provisioning.

### 5. Security Perspective
Security relies on perimeter defenses and does not follow a zero-trust approach. The cloud architecture should enforce least privilege, segment networks, encrypt data, and enable monitoring. IAM roles, security groups, AWS WAF, and AWS Shield should be implemented for protection, while AWS CloudTrail and GuardDuty provide auditing and threat detection.

### 6. Operations Perspective
Operations are currently manual and reactive, resulting in slow incident handling and inconsistent releases. The organization should adopt monitoring, logging, and automation to enhance operational maturity. Amazon CloudWatch, AWS Systems Manager, and AWS Config can enable proactive monitoring, automated patching, and operational best practices.

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