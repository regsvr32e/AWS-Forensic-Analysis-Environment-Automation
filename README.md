# AWS-Forensic-Analysis-Environment-Automation

  <img width="1024" height="512" alt="readme_cover" src="https://github.com/user-attachments/assets/8c535277-51b8-451f-8f7b-bb39e47101c2" />


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
```
Deploy infrastructure:

# Using Terraform
cd infrastructure/terraform
terraform init && terraform apply

# Using CloudFormation
aws cloudformation deploy \
  --template-file infrastructure/cloudformation/main.yaml \
  --stack-name forensic-automation


Publish a Lambda function:

cd lambdas/snapshot_collector
zip -r function.zip .
aws lambda update-function-code \
  --function-name SnapshotCollector \
  --zip-file fileb://function.zip


Run a forensic script with SSM:

aws ssm send-command \
  --targets "Key=instanceIds,Values=<INSTANCE_ID>" \
  --document-name "<SSM_DOCUMENT_NAME>"

Example Use Cases

Automating forensic snapshot collection after GuardDuty or Security Hub findings

Running SSM scripts for host triage (network connections, process listings, volatile data)

Building forensic baselines by scheduling repeated evidence collection

Security and Chain of Custody

Evidence is stored in a dedicated S3 bucket with encryption and strict access controls

Snapshots and logs are tagged for correlation with incidents

Metadata and hashing are captured where applicable to maintain integrity

Contributing

Contributions are welcome. Open an issue before submitting major changes, and include documentation updates with pull requests.

License

This project is licensed under the MIT License. See the LICENSE file for details.
