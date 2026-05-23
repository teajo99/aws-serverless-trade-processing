#  Trade Processing & Compliance System (AWS Serverless Architecture)

## Overview

This project simulates a **financial trade processing platform** used in banking and trading environments.

It is designed to process end-of-day (EOD) trades, validate compliance rules, and distribute results to multiple downstream financial systems in real time.

The system is fully serverless and event-driven, built using AWS managed services.

---

## Financial Architecture

Market Trades (Simulated Batch Input)
↓
EventBridge (EOD Scheduler Trigger)
↓
TradeProcessorLambda (Trade Processing Engine)
↓
SNS Topic (Financial Event Bus)
┌──────────────┬──────────────┬──────────────┐
↓ ↓ ↓
Compliance Queue Risk Engine Client Notifications
(SQS) (Lambda) (Email)


---

##  Business Use Case

In real financial institutions:

- Trades are executed throughout the day
- End-of-day systems process all trades in batch
- Compliance checks ensure regulatory rules are met
- Risk systems analyze exposure
- Reports are distributed to stakeholders

This project replicates that entire workflow using AWS serverless services.

---

##  AWS Services Used

- **AWS Lambda** → Trade processing + risk analysis
- **Amazon EventBridge** → Scheduled EOD trigger
- **Amazon SNS** → Financial event distribution bus
- **Amazon SQS** → Compliance message queue
- **Amazon CloudWatch** → Logging and audit trail

---

## System Workflow

1. EventBridge triggers the system on a schedule (EOD simulation)
2. `TradeProcessorLambda` processes trade batch
3. Compliance and validation logic is executed
4. Results are published to SNS (financial event bus)
5. SNS distributes messages to:
   - SQS queue (Compliance system)
   - Risk analysis Lambda (risk engine)
   - Email notifications (client reporting)

---

##  Project Structure

aws-serverless-trade-processing/

├── trade_processor.py # Core trade processing engine
├── risk_analysis.py # Risk analysis service
├── README.md # Project documentation

├── screenshots/ # AWS execution evidence
├── docs/ # Architecture diagrams


---

##  Key Financial Features

- End-of-day trade processing simulation
- Event-driven financial messaging system
- Multi-system distribution (risk, compliance, reporting)
- Decoupled microservice architecture
- Audit logging via CloudWatch
- Scalable serverless design (no infrastructure management)

---

##  Error Handling Insight

### Issue Encountered
KeyError: 'Records'


### Cause

The Risk Lambda was tested manually using the AWS Lambda console, which does not include the SNS event structure.

### Fix

The correct execution path is:
TradeProcessorLambda → SNS → RiskAnalysisLambda


SNS automatically provides the correct event format.

---

##  Architecture Characteristics

- Event-driven architecture
- Serverless and scalable design
- Highly decoupled system components
- Real-world financial workflow simulation
- Production-style messaging pattern (SNS fan-out)

---

##  What This Project Demonstrates

This system reflects patterns used in:

- Investment banking systems
- Trading platforms
- Risk management engines
- Financial compliance systems
- Distributed event processing pipelines

---

##  Resume Summary

Built a serverless event-driven financial trade processing system on AWS using EventBridge, Lambda, SNS, and SQS to simulate end-of-day trade workflows with compliance validation, risk analysis, and distributed reporting.

---

##  Screenshots

Include the following in `/screenshots`:

- EventBridge rule configuration
- Lambda function code
- CloudWatch logs (execution proof)
- SNS topic and subscriptions
- SQS messages
- Risk Lambda logs



