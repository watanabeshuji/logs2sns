# Overview
logs2sns is CloudFormation template for Lambda function 
that notify event with email using CloudWatchLogs subscription filter.

# Usage
Login to AWS management console and create CloudFormation stack with logs2sns.yml(logs2sns2.yml).
See: http://dev.classmethod.jp/cloud/aws/notify-error-cloudwatch-logs-with-lambda/ 

# Standard logs2sns
Standard logs2sns has one FilterPattern and one SNS Topic.

## CloudFormation Parameters
- FilterPattern: Log pattern to notify
- FilterPatternExcluded: Log exclude pattern to notify
- MailSubject: Subject of notify mail
ｰ NotifyTopicNameWarning: SNS topic name for notify.
- LogGroupName: CloudWatch Logs log group name.
- FilterPatternForSubScription: Filter pattern for CloudWatch Logs subscription.

# 2way logs2sns
2way logs2sns has two set of FilterPattern and one SNS Topic.
One is warning filter and other is error filter.

## CloudFormation Parameters
- ErrorFilterPattern: Error log pattern to notify
- ErrorFilterPatternExcluded: Error log exclude pattern to notify
- ErrorMailSubject: Subject of error notify mail
ｰ ErrorNotifyTopicName: SNS topic name for error notify.
- WarningFilterPattern: Warning log pattern to notify
- WarningFilterPatternExcluded: Warning log exclude pattern to notify
- WarningMailSubject: Subject of warning notify mail
ｰ WarningNotifyTopicName: SNS topic name for warning notify.
- LogGroupName: CloudWatch Logs log group name.
- FilterPatternForSubScription: Filter pattern for CloudWatch Logs subscription.

# How it works?
- Create SNS Topic with email subscription.
- Create IAM Role for Lambda function.
- Create Lambda function process CloudWatch Logs streaming event (filter and notify email).
- Add permission to Lambda function to invoke from CloudWatch Logs
- Create CloudWatch Logs subscription filter that sends log data to the AWS Lambda function

# Licence
- The MIT License (MIT)
