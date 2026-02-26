# AWS Well-Architected and Cloud Adoption Frameworks Evaluation

## Overview

This repository contains the deliverables for the "Design and Evaluate an AWS Solution Using the Well-Architected and Cloud Adoption Frameworks" lab. The project focuses on assessing and planning the migration of a legacy, on-premises two-tier web application (frontend servers and backend database) into Amazon Web Services (AWS) using recognized best practices and architectural standards.

## Deliverables

According to the lab requirements, three main deliverables are provided:

1.  **[aws_waf_caf_assessment.md](aws_waf_caf_assessment.md)**: 
    *   **WAF Assessment Table (Task 2):** Evaluates the operational, security, reliability, performance, and cost pillars. Detailed observations of the on-premises architecture limitations are paired with recommendations utilizing explicit AWS services.
    *   **CAF Readiness Summary (Task 3):** Offers a comprehensive analysis across the six CAF perspectives (Business, People, Governance, Platform, Security, and Operations) identifying enablers necessary for successful enterprise migration.
    *   **Reflection:** A 150-word summary emphasizing the shift from legacy physical infrastructure management to holistic, cloud-native operational paradigms learned throughout the module.
2.  **[architecture_diagram.md](architecture_diagram.md)**: 
      ![cloud architecture diagram](cloud_architecture.png)
    *   **Improved Architecture Diagram (Task 4):** A fully-rendered Mermaid flow diagram outlining the modernized cloud topology. The architecture implements Multi-AZ redundancies natively, leveraging scalable EC2 Auto Scaling Groups and managed Amazon RDS deployments inside a Virtual Private Cloud (VPC) adhering securely to the Well-Architected Framework guidelines.

## Approach Description

The approach for this lab was meticulously structured around translating static, physically-constrained on-premises resources into highly elastic, fault-tolerant cloud services:

*   **Deconstruct the Problem:** First, the limitations of the classic two-tier on-prem application were defined—primarily identifying its single point of failure status, high upfront hardware costs, and heavy operational (manual) burdens.
*   **Evaluate against the WAF:** The five pillars of the WAF were methodically compared against the current on-prem deployment. Recommendations focused directly on remediating single-AZ flaws using Load Balancing, Auto Scaling, and adopting a managed database strategy with Amazon Multi-AZ RDS.
*   **Align via the CAF:** Implementing purely technical changes is rarely enough for a successful enterprise migration. The CAF guidelines were deployed to consider non-technical (Business, People, Governance) implementations necessary to execute a successful, fully supported internal shift to AWS platforms.
*   **Architect and Document:** Using standardized Mermaid rendering capabilities, the theoretical assessments were converted into a tangible logical diagram that visibly demonstrated VPC boundary restrictions, fault segregation (AZ configurations), and traffic flows.

## How to View

*   Standard markdown previewers (native to GitHub, VS Code, or GitLab) support viewing the textual and tabular responses inside the `aws_waf_caf_assessment.md` document.
*   The Architecture diagram in `architecture_diagram.md` utilizes Mermaid.js syntax. Most modern markdown platforms render this block dynamically as an image graphic directly within the documentation.
