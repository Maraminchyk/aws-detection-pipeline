# AWS Threat Detection Pipeline

## Overview

This project demonstrates the implementation of an AWS-based security monitoring and threat detection pipeline.

The solution collects AWS audit and network telemetry, forwards events through a scalable messaging pipeline, ingests logs into Splunk Enterprise, and detects suspicious activity using custom detection rules validated through attack simulation.

## Architecture

CloudTrail + GuardDuty + VPC Flow Logs

↓

Amazon S3

↓

Amazon SNS

↓

Amazon SQS

↓

Splunk Enterprise

↓

Custom Detection Rules

↓

Security Alerts

## Technologies

* AWS CloudTrail
* AWS GuardDuty
* AWS VPC Flow Logs
* Amazon S3
* Amazon SNS
* Amazon SQS
* Docker
* Splunk Enterprise
* Stratus Red Team

## Key Features

* Multi-region CloudTrail logging
* Centralized log storage in Amazon S3
* Event-driven ingestion using SNS and SQS
* Splunk-based monitoring and analytics
* MITRE ATT&CK mapped detection rules
* Attack simulation and validation

## Detection Coverage

* CloudTrail Tampering
* Logging and Monitoring Disabled
* IAM Persistence Activity
* Credential and Secret Access
* Snapshot Exfiltration and Risky Access Exposure

## Skills Demonstrated

AWS • Linux • Docker • Splunk • Security Monitoring • Threat Detection • Cloud Security • Detection Engineering • Incident Analysis
