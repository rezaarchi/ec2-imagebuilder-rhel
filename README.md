# Automating STIG Compliance with the Latest Red Hat Packages for RHEL 8 on AWS EC2 Instances using Image Pipeline and CloudFormation

## Overview

This project automates the creation of STIG-compliant Amazon Machine Images (AMIs) for Red Hat Enterprise Linux 8 (RHEL 8) EC2 instances on AWS. By leveraging EC2 Image Builder, the latest STIG packages from Red Hat, and CloudFormation, this solution simplifies and streamlines the process of ensuring your EC2 instances meet the latest STIG compliance requirements.

## Benefits
- **Security**: Ensures EC2 instances are in line with the latest STIG security controls and industry standards.
- **Automation**: Automates the creation of STIG-compliant instances, saving time and effort.
- **Consistency**: Ensures that all EC2 instances are built using the same STIG-compliant image, reducing configuration drift and simplifying ongoing management.
- **Compliance**: Helps meet regulatory requirements by ensuring your EC2 instances align with security standards required by the US Department of Defense.

## Key Components

### EC2 Image Builder
EC2 Image Builder is a fully managed service that simplifies the creation, maintenance, and validation of Amazon Machine Images (AMIs) for EC2 instances. It automates the creation of custom AMIs and integrates with other AWS services like EC2 Auto Scaling, AWS CloudFormation, and AWS CodePipeline.

### CloudFormation Script
This repository contains a CloudFormation script that automates the entire process:
1. Downloads the latest STIG Ansible playbook.
2. Applies the playbook to an EC2 RHEL 8 instance.
3. Creates an AMI from the STIG-compliant instance.
4. The created AMI can then be used to launch new EC2 instances that are already compliant with the latest STIG requirements.

### Latest Red Hat STIG Packages
By using the most up-to-date Red Hat STIG packages, this solution ensures your EC2 instances are aligned with the latest security fixes and vulnerability mitigations.

## Prerequisites
- **AWS Account**: An active AWS account.
- **IAM Permissions**: Appropriate IAM roles and policies to deploy EC2 Image Builder and CloudFormation resources.
- **RHEL 8 Instance**: EC2 RHEL 8 instance to apply the STIG playbook.
- **Ansible**: Ensure Ansible is configured to apply the Red Hat STIG playbook.

## Getting Started

# STIG-Compliant EC2 Image Builder

## Getting Started

### 1. Clone the Repository

Clone this repository to your local machine:

```bash
git clone <repository-url>
cd <repository-directory>
```

### 2. Configure CloudFormation Stack

Deploy the CloudFormation stack that will create the EC2 Image Builder pipeline and apply the latest STIG playbook. This will also set up the necessary resources for the STIG-compliant image creation.

```bash
aws cloudformation deploy --template-file image-pipeline.yml --stack-name stig-compliant-image-pipeline --capabilities CAPABILITY_NAMED_IAM
```

### 3. Monitor Image Creation

After deploying the CloudFormation stack, the EC2 Image Builder pipeline will automatically create the STIG-compliant AMI. You can monitor the progress in the EC2 Image Builder console:

1. Go to the EC2 Image Builder section in the AWS Management Console
2. Track the pipeline's progress as it applies the latest STIG packages and creates the AMI

### 4. Launch STIG-Compliant EC2 Instances

Once the AMI is created, you can use it to launch EC2 instances that are compliant with the latest STIG requirements:

1. Go to the EC2 Console
2. Select **Launch Instance**
3. Under the AMIs section, select the newly created AMI
4. Follow the usual EC2 instance launch steps to start a new instance with the STIG-compliant image

## Solution Workflow

1. **CloudFormation**: Launches EC2 Image Builder pipeline with the required parameters
2. **EC2 Image Builder**: Downloads the latest STIG Ansible playbook, applies it to a RHEL 8 EC2 instance
3. **STIG Playbook**: Ensures that the EC2 instance meets the latest STIG compliance for RHEL 8
4. **AMI Creation**: Once the instance is compliant, an AMI is created
5. **Future Use**: The resulting AMI can be used to launch additional STIG-compliant EC2 instances

## Cleanup

To remove the created resources after use, delete the CloudFormation stack:

```bash
aws cloudformation delete-stack --stack-name stig-compliant-image-pipeline
```

## Summary

By automating the process of creating STIG-compliant RHEL 8 instances with EC2 Image Builder, this solution significantly reduces the complexity and time required for compliance. It ensures that all EC2 instances are secure, consistent, and meet the required security standards. The integration with CloudFormation provides a seamless experience for creating and managing compliant AMIs.
AMI Creation: Once the instance is compliant, an AMI is created.

Future Use: The resulting AMI can be used to launch additional STIG-compliant EC2 instances.

## Cleanup
To remove the created resources after use, delete the CloudFormation stack:

aws cloudformation delete-stack --stack-name stig-compliant-image-pipeline

## Summary
By automating the process of creating STIG-compliant RHEL 8 instances with EC2 Image Builder, this solution significantly reduces the complexity and time required for compliance. It ensures that all EC2 instances are secure, consistent, and meet the required security standards. The integration with CloudFormation provides a seamless experience for creating and managing compliant AMIs.
