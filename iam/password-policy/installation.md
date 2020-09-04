# Community::IAM::PasswordPolicy

## Installation using AWS CLI
``` bash
# first install the execution role
aws cloudformation create-stack \
  --template-url https://community-resource-provider-catalog.s3.amazonaws.com/community-iam-passwordpolicy-resource-role-0.1.0.yml \
  --stack-name community-iam-passwordpolicy-resource-role \
  --capabilities CAPABILITY_IAM

aws cloudformation wait stack-create-complete \
  --stack-name community-iam-passwordpolicy-resource-role

# get the value of the ExecutionRoleArn Output
aws cloudformation describe-stacks \
  --stack-name community-iam-passwordpolicy-resource-role

# register the cloudformation type
aws cloudformation register-type \
  --type-name Community::IAM::PasswordPolicy \
  --type RESOURCE \
  --schema-handler-package s3://community-resource-provider-catalog/community-iam-passwordpolicy-0.2.0.zip

aws cloudformation describe-type-registration --registration-token <registration-token> 

aws cloudformation set-type-default-version \
  --version-id <version-id> \
  --type-name Community::IAM::PasswordPolicy \
  --type RESOURCE

```