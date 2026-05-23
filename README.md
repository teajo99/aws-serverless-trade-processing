# AWS Serverless Trade Processing System

## Overview

A fully serverless event-driven system built on AWS that simulates nightly financial trade processing.

It processes trades automatically, validates compliance, and distributes results using SNS fan-out architecture.

---

## Architecture

EventBridge → Lambda → SNS → SQS + Email + Lambda

---

## AWS Services Used

- AWS Lambda (compute)
- Amazon EventBridge (scheduler)
- Amazon SNS (message distribution)
- Amazon SQS (queue system)
- Amazon CloudWatch (logging)

---

## How It Works

1. EventBridge triggers the system on a schedule
2. TradeProcessorLambda processes simulated trade data
3. Results are published to SNS topic
4. SNS distributes messages to:
   - Email subscribers
   - SQS queue (compliance system)
   - RiskAnalysis Lambda

---

## Project Structure

aws-serverless-trade-processing/

├── trade_processor.py  
├── risk_analysis.py  
├── README.md  

---

## Key Features

- Fully serverless architecture
- Event-driven automation
- SNS fan-out messaging pattern
- Scalable design (no servers required)
- Real-time distributed processing

---

## Common Issue Fixed

While testing the Risk Lambda manually, an error occurred:

"KeyError: 'Records'"

This happened because SNS event structure was missing when using manual Lambda testing.

Fix:
- Proper testing was done through SNS-triggered invocation instead of direct Lambda test.

---

## What I Learned

- AWS event-driven architecture
- Serverless computing concepts
- SNS fan-out pattern
- Lambda event handling
- CloudWatch logging and debugging

---

## Resume Summary

Built a serverless AWS trade processing system using EventBridge, Lambda, SNS, and SQS to automate financial workflows and multi-system event distribution.
