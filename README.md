# AWS-Forensic-Analysis-Environment-Automation

<p align="center">
  <img width="512" height="512" alt="readme_cover" src="https://github.com/user-attachments/assets/8c535277-51b8-451f-8f7b-bb39e47101c2" />
</p>

This repository contains tools, scripts, and infrastructure templates for automating forensic data acquisition and analysis in AWS environments.  
It includes Lambda functions, PowerShell and Bash scripts, and Infrastructure as Code (CloudFormation and Terraform) to support forensic workflows.

## Overview

Incident response in AWS requires fast and repeatable methods for collecting evidence. This project provides automation for:

- Collecting and preserving EC2 instance and EBS volume snapshots
- Automating snapshot workflows with Lambda and Step Functions
- Running SSM-based acquisition scripts on Windows and Linux hosts
- Deploying supporting infrastructure through CloudFormation or Terraform

The purpose of this repository is to share a forensic workflow automation that is modular and doesn't require SSM enabled on every system to be able to start forensicating.
Also, to document and save my work.


## Getting Started

### Prerequisites
- AWS account with sufficient IAM permissions  
- AWS CLI configured locally  
- Terraform or CloudFormation tools installed  
- SSM Agent running on target EC2 instances  

### Deployment

Clone the repository:
```bash
git clone https://github.com/<your-org>/aws-forensic-automation.git
cd aws-forensic-automation
