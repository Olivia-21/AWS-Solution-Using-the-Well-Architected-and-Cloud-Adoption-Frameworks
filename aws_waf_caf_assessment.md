# AWS Well-Architected & Cloud Adoption Framework Assessment

## Task 1 – Review the Existing Architecture

**Background:** 
The organization is migrating a two-tier web application (frontend + backend database) from on-premises servers to AWS. 

**Component Identification:**
1. **Frontend Layer:** On-premises web/application servers hosting the frontend.
2. **Backend Layer:** On-premises database servers running the backend data tier.

**Potential Risks & Weaknesses:**
* **Lack of High Availability:** The on-premises setup is likely running in a single data center (acting as a single point of failure), risking downtime during hardware failures or local outages.
* **Limited Scalability:** Fixed resources mean the environment cannot elastically scale to meet traffic spikes, leading to potential performance bottlenecks.
* **Backup & DR Gaps:** No clearly defined automated backup strategy or disaster recovery (DR) environment.
* **Security & Maintenance Overhead:** Manual security patching, potential open network security groups, and lack of fine-grained network segregation increases the system's vulnerability envelope.

---

## Task 2 – Evaluate the Workload Using the AWS Well-Architected Framework

| Pillar | Observation | Improvement Recommendation | Supporting AWS Service |
| :--- | :--- | :--- | :--- |
| **Operational Excellence** | Manual updates, patching, and deployments on-premises are error-prone and time-consuming. | Automate infrastructure provisioning, configuration, and application deployments using Infrastructure as Code (IaC). | AWS CloudFormation, AWS Systems Manager, AWS CodePipeline |
| **Security** | Potential gaps in encryption at rest and in transit, and flat network structures. | Implement a defense-in-depth strategy, encrypt all data, restrict traffic with private subnets, and use least privilege access. | AWS Identity and Access Management (IAM), AWS KMS, Amazon VPC Security Groups |
| **Reliability** | Single point of failure; relies on manual failover without a defined backup or DR strategy. | Architect for high availability across multiple physical locations and implement automated, synchronized database backups. | Amazon EC2 Auto Scaling, Elastic Load Balancing (ELB), Multi-AZ Amazon RDS |
| **Performance Efficiency** | Fixed, heavily over-provisioned or under-provisioned on-premises resources that can't quickly adapt. | Adopt elastic computing to scale resource capacity dynamically based on metrics like CPU usage or network traffic. | Amazon EC2 Auto Scaling, Amazon CloudFront |
| **Cost Optimization** | High upfront capital expenditure for hardware that may be significantly underutilized during off-peak times. | Shift to a pay-as-you-go model, correctly size resources, and set up billing alerts to avoid cost overruns. | AWS Cost Explorer, AWS Budgets, AWS Compute Optimizer |

---

## Task 3 – Apply the AWS Cloud Adoption Framework (CAF)

**Business Perspective**
The migration of this two-tier web application must align tightly with the organization's broader business goals. By transitioning to AWS, the business moves from a CapEx (capital expenditure) model to an OpEx (operational expenditure) model, freeing up capital that would otherwise be locked in physical hardware. This migration targets reducing the time-to-market for new features and improving overall customer satisfaction by minimizing downtime. Key actions include engaging business stakeholders to establish clear KPIs—such as application uptime, user latency, and infrastructure cost per transaction—ensuring the technical migration translates into measurable business value, agility, and risk reduction.

**People Perspective**
Successful cloud adoption requires preparing the workforce for a new paradigm. The organization needs to assess existing technical skills and upskill on-premises server administrators into Cloud Architects, SysOps Administrators, and DevOps Engineers. An established AWS training and certification plan is critical. Creating a Cloud Center of Excellence (CCoE) will help evangelize best practices across teams and manage cultural shifts. Clear communication regarding changing job roles and responsibilities will alleviate anxiety and foster a culture of continuous learning and innovation within the IT department.

**Governance Perspective**
Governance ensures that cloud initiatives are managed and controlled effectively while minimizing risks. Moving to AWS requires updating IT governance policies. The organization must define robust cloud policies including resource tagging schemas, cost allocation, and strict security guardrails. Implementing a landing zone approach with AWS Control Tower to manage multiple AWS accounts will allow the organization to deploy standardized security constraints. Additionally, establishing strict financial oversight and budgeting disciplines is crucial to prevent resource sprawl and unexpected billing overruns post-migration.

**Platform Perspective**
This perspective focuses on the architecture and delivery of cloud services. Migrating a two-tier app represents an opportunity to shift from legacy static servers to a modern, scalable infrastructure. The organization must define an architecture relying on managed services (like Amazon RDS) to offload undifferentiated heavy lifting. The platform strategy should emphasize standardizing the deployment models, ensuring high availability, and building a foundation that complies with the AWS Well-Architected Framework. Automation of the environment through infrastructure as code will establish an agile, consistent, and repeatable platform.

**Security Perspective**
Securing the workload changes significantly when shifting from a physical data center to the cloud. Security must be integrated into every tier (DevSecOps). The organization must map out strict identity management policies using IAM for least-privilege access. The network must be hardened using Amazon VPC, segmenting public-facing load balancers from private application and database tiers. Strong data protection mandates the use of encryption at rest (KMS) and in transit (TLS/SSL). Furthermore, the organization must establish robust incident response plans tailored to an AWS environment to rapidly mitigate threats.

**Operations Perspective**
Moving to the cloud necessitates transitioning from manual operations to automated, software-driven operational health management. The focus shifts towards continuous integration, continuous delivery (CI/CD), and robust monitoring. Introducing Amazon CloudWatch and AWS CloudTrail will give operations teams deep visibility into the application’s telemetry, performance metrics, and API activity. The operations teams must develop runbooks for automated recovery and configure automated alerts to respond to incidents proactively, ensuring that the application meets its Service Level Agreements (SLAs) with minimal manual intervention.

---

## Task 4 – Design an Improved Architecture

Please refer to the `architecture_diagram.md` for the visual architecture and detailed component breakdown.

**High-Level Summary:**
The revised architecture shifts the workload to an AWS multi-AZ environment within a Virtual Private Cloud (VPC), directly addressing the WAF pillars:
* An **Application Load Balancer** distributes traffic across multiple Availability Zones.
* **EC2 Auto Scaling Groups** run the frontend in private subnets, dynamically adjusting capacity.
* **Amazon RDS with Multi-AZ** handles the backend database securely and reliably, replicating data across zones for automatic failover.

---

## Deliverable: Brief Reflection

Through this lab, I learned how to systematically evaluate a legacy architecture and design a modernized cloud equivalent using the AWS Well-Architected Framework (WAF) and Cloud Adoption Framework (CAF). Migrating a two-tier application isn't just about 'lifting and shifting' servers; it's an opportunity to embrace cloud-native features like elastic scaling, automated failover, and managed databases. I gained deeper insights into how the WAF's five pillars guide technical decisions, ensuring the workload is secure, highly available, and cost-effective. Furthermore, applying the CAF perspectives helped me realize that technical changes must be accompanied by organizational readiness—involving people, governance, and business alignment. This structured evaluation perfectly bridges the gap between business objectives and technical implementation, empowering me as a cloud architect to present clear, justifiable recommendations for AWS adoption and future transformation.
