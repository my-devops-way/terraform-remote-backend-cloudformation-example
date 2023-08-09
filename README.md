# terraform-remote-backend-cloudformation-example
Example for deploying an S3 bucket and a DynamoDB table to be used as remote backend for terraform.
# S3 and Dynamodb example using CloudFormation

## create stack

```bash
aws cloudformation create-stack \
--stack-name <stack name> \
--parameters file://parameters.json \
--template-body file://terraform-remote-backend.yaml
```

## create change set

```bash
aws cloudformation create-change-set \
--stack-name <stack name> \
--change-set-name  dynamodb \
--parameters=file://parameters.json \
--template-body file://terraform-remote-backend.yaml
```

## describe change set

```bash
aws cloudformation describe-change-set \
--change-set-name <change set name>\
--stack-name hatimtest
```

## execute change set

```bash
aws cloudformation execute-change-set \
--change-set-name <change set name> \
--stack-name <stack name>
```

## delete stack

```bash
aws cloudformation delete-stack \
--stack-name my-stack
```
