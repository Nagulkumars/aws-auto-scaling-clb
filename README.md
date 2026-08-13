# AWS EC2 Auto Scaling with Classic Load Balancer

## Project Overview

This project demonstrates an AWS EC2 Auto Scaling environment integrated with a Classic Load Balancer in the AWS Ireland (`eu-west-1`) region.

The implementation used a custom AMI and an EC2 Launch Template to standardize instance configuration. An Auto Scaling Group was then created using the launch template, with load balancer integration and multi-AZ networking. The deployment was verified through EC2 instance states, Auto Scaling activity, and the load balancer endpoint.

> **Detailed evidence:** The complete 28-screenshot implementation is documented in the accompanying Word and PDF project documentation.

---

## Architecture

```text
                         AWS Ireland (eu-west-1)
                                  │
                         ┌────────┴────────┐
                         │                 │
                    Classic Load      Auto Scaling
                     Balancer            Group
                         │                 │
                         │          ┌──────┼──────┐
                         │          │      │      │
                         │        AZ-1   AZ-2   AZ-3
                         │          │      │      │
                         └──────── EC2    EC2    EC2
                                    ▲      ▲      ▲
                                    └── Launch Template ──┐
                                                         │
                                                         AMI
```

### Architecture Explanation

- **VPC-01** provides the networking environment.
- **Internet Gateway and route table** provide public connectivity for the web-server environment.
- **Subnets across Availability Zones** support a multi-AZ deployment.
- **AMI (`ASG-Master-Image`)** provides the reusable server image.
- **Launch Template (`ASG_Template`)** standardizes EC2 instance configuration.
- **Auto Scaling Group (`ASG`)** manages the EC2 instance fleet and desired capacity.
- **Classic Load Balancer (`ASG-CLB`)** distributes incoming traffic across the instances.
- The final application was verified through the Classic Load Balancer endpoint.

---

## AWS Services Used

- Amazon EC2
- Amazon Machine Image (AMI)
- EC2 Launch Templates
- EC2 Auto Scaling
- Classic Load Balancer
- Amazon VPC
- Subnets
- Route Tables
- Internet Gateway

---

## Project Objectives

- Create a reusable AMI for EC2 server deployment.
- Create a Launch Template for consistent instance configuration.
- Configure an Auto Scaling Group.
- Integrate the Auto Scaling Group with a Classic Load Balancer.
- Use multiple Availability Zones for the EC2 deployment.
- Observe Auto Scaling activity and instance replacement.
- Verify the application through the load balancer endpoint.

---

## Implementation

### 1. VPC and Networking

The project used **VPC-01** in the AWS Ireland (`eu-west-1`) region. The networking setup included a subnet, Internet Gateway, route table, and subnet association.

### 2. AMI

A custom AMI named **`ASG-Master-Image`** was used as the reusable base image for instances launched through the Auto Scaling environment.

### 3. Launch Template

A launch template named **`ASG_Template`** was created to maintain consistent EC2 configuration whenever Auto Scaling launches new instances.

### 4. Classic Load Balancer

A Classic Load Balancer named **`ASG-CLB`** was created to distribute incoming traffic across EC2 instances in multiple Availability Zones.

### 5. Auto Scaling Group

An Auto Scaling Group named **`ASG`** was created using the launch template. The configuration included group capacity settings and integration with the Classic Load Balancer.

### 6. Scaling and Instance Verification

The EC2 console and Auto Scaling activity history were used to observe instances being launched, terminated, and replaced during the Auto Scaling workflow.

### 7. Application Verification

The final load balancer DNS endpoint was accessed to verify that the Auto Scaling web application was reachable.

---

## Key Learning Outcomes

- Understanding the relationship between **AMI → Launch Template → Auto Scaling Group → EC2 instances**.
- Understanding how a Classic Load Balancer can distribute traffic across multiple EC2 instances.
- Understanding multi-AZ EC2 deployment.
- Understanding Auto Scaling Group capacity and instance lifecycle management.
- Observing Auto Scaling activity and health-related instance replacement.
- Understanding how reusable instance configuration supports automated deployment.

---

## Skills Demonstrated

`AWS EC2` `AMI` `Launch Templates` `Auto Scaling` `Classic Load Balancer` `VPC` `Subnets` `Route Tables` `Internet Gateway` `Multi-AZ Deployment` `Cloud Networking`

---

## Interview Summary

I created an Auto Scaling environment in the AWS Ireland region using a custom AMI and an EC2 Launch Template. The launch template was used by the Auto Scaling Group to maintain a consistent configuration when launching instances. I integrated the Auto Scaling Group with a Classic Load Balancer so incoming traffic could be distributed across the EC2 instances. I also used multiple Availability Zones and verified the environment through EC2 instance states, Auto Scaling activity history, and the load balancer DNS endpoint.

### If asked: "Why use a Launch Template?"

A Launch Template provides a reusable configuration for launching EC2 instances. In this project, the Auto Scaling Group used the template so newly launched instances followed the same server configuration.

### If asked: "Why use Auto Scaling with a Load Balancer?"

Auto Scaling manages the number and lifecycle of EC2 instances, while the Load Balancer distributes incoming traffic across the available instances. Together they improve availability and help the application handle changing demand.

### If asked: "What happens when an instance becomes unhealthy?"

The Auto Scaling Group can detect an unhealthy instance through its configured health checks and replace it to maintain the desired capacity.

---

## Project Outcome

Successfully demonstrated an EC2 Auto Scaling environment using a reusable AMI, Launch Template, Classic Load Balancer, multi-AZ deployment, and Auto Scaling Group. The setup was verified through AWS console activity, EC2 instance changes, and the final load balancer endpoint.

---

## Documentation

- [Complete Project Documentation - Word](./AWS-Auto-Scaling-Project-Documentation.docx)
- [Complete Project Documentation - PDF](./AWS-Auto-Scaling-Project-Documentation.pdf)

---

## Screenshot Evidence

The original uploaded evidence contains **28 screenshot placements**. The detailed documentation preserves the project workflow in the required reverse order (bottom-to-top from the uploaded Word document).
