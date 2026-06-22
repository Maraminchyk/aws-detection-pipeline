# aws-detection-pipeline
AWS Security Monitoring Pipeline with CloudTrail, GuardDuty, Splunk and Stratus Red Team
# AWS Detection Pipeline & Security Monitoring

## Overview

This project demonstrates the implementation of a cloud security monitoring pipeline in AWS.

The solution collects and processes security events from multiple AWS services and ingests them into Splunk for monitoring and threat detection.

## Documentation

Detailed implementation steps, configuration screenshots and validation results are available in:

- architecture/architecture-explanation.md
## Screenshots

Implementation screenshots are available in the screenshots directory.

## Architecture

CloudTrail + GuardDuty + VPC Flow Logs
            ↓
            S3
            ↓
           SNS
            ↓
           SQS
            ↓
         Splunk
## Infrastructure Components

The monitoring pipeline was built using:

- Amazon S3 for centralized log storage
- Multi-region AWS CloudTrail for audit logging
- Amazon GuardDuty for threat detection
- VPC Flow Logs for network telemetry
- Amazon SNS and SQS for event delivery
- Splunk Enterprise for log ingestion and analysis

## Technologies

- AWS CloudTrail
- AWS GuardDuty
- AWS VPC Flow Logs
- Amazon S3
- Amazon SNS
- Amazon SQS
- Docker
- Splunk Enterprise
- Stratus Red Team

## Key Features

- Centralized log collection
- Automated event ingestion
- Security monitoring
- Detection rule development
- MITRE ATT&CK mapping
- Attack simulation

## Skills Demonstrated

- AWS
- Linux
- Docker
- Terraform
- Splunk
- Security Monitoring
- Threat Detection
- Cloud Security

## Lessons Learned

- Building cloud monitoring pipelines
- Working with AWS logging services
- Security event analysis
- Detection engineering fundamentals
