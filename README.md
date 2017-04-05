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
- MailSubject: Subject of notify mail
ｰ NotifyTopicNameWarning: SNS topic name for notify.

# 2way logs2sns
2way logs2sns has two set of FilterPattern and one SNS Topic.
One is warning filter and other is error filter.

## CloudFormation Parameters
- FilterPatternError: Error log pattern to notify
- MailSubjectError: Subject of error notify mail
ｰ NotifyTopicNameError: SNS topic name for error notify.
- FilterPatternWarning: Warning log pattern to notify
- MailSubjectWarning: Subject of warning notify mail
ｰ NotifyTopicNameWarning: SNS topic name for warning notify.

# How it works?
- Create SNS Topic with email subscription.
- Create IAM Role for Lambda function.
- Create Lambda function process CloudWatch Logs streaming event (filter and notify email).
- Add permission to Lambda function to invoke from CloudWatch Logs

# Licence
- The MIT License (MIT)
