# AWS Serverless Trade Processing System

## What This Project Does

This project simulates a financial trade processing system using AWS serverless services.

Every scheduled run:

1. EventBridge triggers the system
2. Lambda processes trades (trade_processor.py)
3. Results are published to SNS
4. SNS distributes messages to:
   - Email notifications
   - SQS compliance queue
   - Risk analysis Lambda

---

## Architecture

EventBridge  
→ Lambda (Trade Processor)  
→ SNS Topic  
→ Email + SQS + Risk Lambda  

---

## AWS Services Used

- AWS Lambda
- Amazon EventBridge
- Amazon SNS
- Amazon SQS
- CloudWatch Logs

---

## Key Learning

- Event-driven architecture
- Serverless computing
- Fan-out messaging pattern
- Real-time distributed processing