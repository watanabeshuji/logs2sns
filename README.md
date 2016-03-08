# Overview
logs2sns is CloudFormation template for Lambda function 
that notify event with email using CloudWatchLogs subscription filter.

# Usage
Login to AWS management console and create CloudFormation stack with logs2sns.template.

## CloudFormation Parameters
- FilterPattern: Log pattern to notify
- NotifyMailAddress: Mail address notify to

# How it works?
- Create SNS Topic with email subscription.
- Create IAM Role for Lambda function.
- Create Lambda function process CloudWatch Logs streaming event (filter and notify email).
- Add permission to Lambda function to invoke from CloudWatch Logs

# Licence
- The MIT License (MIT)
