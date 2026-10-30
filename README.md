# aws-auto-scaling-group-template
CloudFormation template for deploying an Auto Scaling Group (ASG) using an existing EC2 Launch Template, multiple subnets, and an Application Load Balancer (ALB) Target Group.
This template is fully parameterized, reusable, and safe for public GitHub repositories.

## Overview
This project provides an AWS CloudFormation template that creates an Auto Scaling Group capable of launching EC2 instances across multiple Availability Zones. It integrates with an existing ALB Target Group and uses a pre‑configured EC2 Launch Template for instance configuration.
This template is ideal for:
- Learning AWS Infrastructure‑as‑Code (IaC)
- Demonstrating CloudFormation skills in a portfolio
- Deploying scalable EC2 workloads behind an ALB
- Modular AWS architecture setups

## Architecture
The architecture uses an Application Load Balancer to distribute incoming traffic to EC2 instances managed by an Auto Scaling Group across multiple Availability Zones.
  <img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/b01a5ab9-1003-4315-9da1-c1848cd61322" />
  
## Features
- Auto Scaling Group with configurable size
- Multi‑AZ deployment using a list of subnet IDs
- Integration with an existing ALB Target Group
- Uses an existing EC2 Launch Template
- Clean, readable YAML
- Validated using aws cloudformation validate-template

## Parameters
| Parameter | Description |
| --- | --- |
| **LaunchTemplateId** | ID of an existing EC2 Launch Template |
| **LaunchTemplateVersion** | Version number of the Launch Template |
| **SubnetIds** | List of subnet IDs where ASG instances will launch |
| **TargetGroupArn** | ARN of an existing ALB Target Group |

## Validate the Template
``aws cloudformation validate-template \
  --template-body file://my-asg-template.yaml \
  --region us-east-1``

## Deployment (Optional)
aws cloudformation create-stack \
  --stack-name MyASGStack \
  --template-body file://cloudformation/my-asg-template.yaml \
  --parameters \
      ParameterKey=LaunchTemplateId,ParameterValue=<your-lt-id> \
      ParameterKey=LaunchTemplateVersion,ParameterValue=<version> \
      ParameterKey=SubnetIds,ParameterValue="subnet-123,subnet-456" \
      ParameterKey=TargetGroupArn,ParameterValue=<your-tg-arn> \
  --region us-east-1``

## Repository Structure
aws-auto-scaling-group-template/
├── README.md
├── architecture/
│   └── aws-asg-architecture.png
└── cloudformation/
    └── my-asg-template.yaml

## Prerequisites
Before deploying this template, ensure you have:
- An AWS account
- AWS CLI installed and configured
- An existing EC2 Launch Template
- An existing Application Load Balancer Target Group
- Two or more subnet IDs
- Appropriate AWS permissions to create and manage Auto Scaling resources

