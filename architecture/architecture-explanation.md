# Architecture Explanation

## Overview

This project implements an AWS-based security monitoring pipeline designed to collect, process, and analyze security events from multiple AWS services. The architecture enables centralized log storage, automated event delivery, security monitoring, and threat detection using Splunk Enterprise.

## Pipeline Components

### CloudTrail

AWS CloudTrail collects audit events across the AWS account. It is configured as a multi-region trail with management events enabled for both read and write operations. This provides visibility into user actions and service activity across all AWS regions.

### Amazon S3

Amazon S3 serves as the centralized storage location for CloudTrail logs. Versioning, server-side encryption (SSE-S3), and Block Public Access are enabled to ensure data integrity, protection, and retention.

### Amazon SNS

Amazon SNS receives notifications whenever new CloudTrail log files are created in S3. These notifications allow events to be automatically forwarded through the monitoring pipeline.

### Amazon SQS

Amazon SQS receives messages from SNS and acts as a buffering layer between AWS services and Splunk. Raw Message Delivery and Long Polling are enabled to improve reliability and event processing efficiency.

### Splunk Enterprise

Splunk Enterprise is deployed in a Docker container and is responsible for log ingestion, indexing, searching, monitoring, and threat detection.

### Splunk Add-on for AWS

The Splunk Add-on for AWS provides integration with AWS services. Using an SQS-Based S3 Input, CloudTrail events are automatically ingested into Splunk and stored in the main index with the sourcetype `aws:cloudtrail`.

### Detection Rules

Five custom detection rules were developed to identify suspicious and potentially malicious activities within the AWS environment.

### Stratus Red Team

Stratus Red Team was used to simulate AWS attack techniques and generate realistic CloudTrail events. A total of 10 attack simulations were executed to validate the monitoring pipeline and detection capabilities.

## Detection Coverage

| Detection Rule                                  | ATT&CK Tactic              | Purpose                                                                     |
| ----------------------------------------------- | -------------------------- | --------------------------------------------------------------------------- |
| CloudTrail Tampering                            | TA0005 - Defense Evasion   | Detects attempts to modify, disable, or interfere with CloudTrail logging.  |
| Logging and Monitoring Disabled                 | TA0005 - Defense Evasion   | Detects actions that reduce visibility by disabling monitoring services.    |
| IAM Persistence Activity                        | TA0003 - Persistence       | Detects creation of new users, credentials, and persistence mechanisms.     |
| Credential and Secret Access                    | TA0006 - Credential Access | Detects access to sensitive secrets and credential storage services.        |
| Snapshot Exfiltration and Risky Access Exposure | TA0010 - Exfiltration      | Detects suspicious snapshot sharing and potential data exposure activities. |

## Validation

The monitoring pipeline was validated using multiple Stratus Red Team attack simulations. Generated CloudTrail events were successfully ingested into Splunk and detected by the implemented rules, demonstrating the effectiveness of the architecture.

## Challenges and Lessons Learned

The most challenging aspect of the project was configuring the integration between Amazon S3, SNS, SQS, and Splunk. Small configuration errors, particularly related to permissions and event notifications, could disrupt the entire ingestion pipeline.

The most valuable learning experience was observing how simulated attacks generated real CloudTrail events and how those events were automatically detected by custom Splunk rules.

Future improvements could include integrating additional AWS log sources, expanding detection coverage, and developing a larger set of MITRE ATT&CK aligned detection rules.
