# AWS_Scheduler_POC
This repository contains a POC implementation of an Amazon EventBridge Cron-based Scheduler that extracts records from PostgreSQL and processes them using AWS Step Functions and AWS Lambda.

## Architecture

### EventBridge Scheduler

Triggers a Step Function workflow based on a predefined cron schedule.

### Step Function Execution

First State: Invokes a Lambda function to extract records from PostgreSQL that need processing. This Lambda returns the records as an array.

Second State (Parallel Processing): Processes records in parallel using a Parallel State.

The parallel state consists of 10 branches, each handling 1 record from the extracted array.

Each record is sent to a Lambda function for processing.

## Components

Amazon EventBridge - Triggers the Step Function at scheduled intervals.

AWS Step Functions - Orchestrates the record extraction and processing.

AWS Lambda - Handles data extraction and processing logic.

PostgreSQL - Stores records that need to be processed.

AWS SAM (Serverless Application Model) - Used for deploying and managing the infrastructure.
