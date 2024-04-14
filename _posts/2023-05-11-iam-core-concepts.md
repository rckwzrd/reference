---
layout: post
iam-docs: https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html
iam-sim: https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_testing-policies.html
iam-yt: https://youtu.be/_ZCTvmaPgao?si=vwc63x_fXAPhC_Pl

---

Identity Access Management is a policy tool used to control access to resources created in AWS. Resources include s3 buckets, lambdas, databases, containers, and other services. Human and application users need allow and deny permissions to perform actions on resources. Permissions are defined in an IAM policy document and attached to a user, group, or role. Notes below cover IAM basics.

[AWS IAM documentation]({{page.iam-docs}})

[AWS IAM policy simulator]({{page.iam-sim}})

[Short video on IAM basics]({{page.iam-yt}})

Create lambda function example
- user creates lambda with lambda::createFunction
- access denied error if user does not have permission
- craft a json policy document and attach to user
	- statement array with effect, action, and resource keys
- effect key: explicit and implicit allow/deny
- resource can include everything or specific resources
- actions on resource are resolved against policy documents attached to user
- execute actions from console, CLI or SDK

Access keys and secret access keys
- secret codes used to interact with aws
- use to configure aws cli and saml2aws
- use to initiate boto3 client
- keys are needed to affiliate policy documents with a user

Policy document
- dynamoDB read only access to specific columns
- asterisk is a wild card
- action key with array of common read only operations
- resource key with table suffix
- condition key with constraint operators and keys to limit scope

Other concepts
- groups for account and organization owners
	- bucket users into admin, developer, and testers
	- apply general or blanket policies
- roles vs users
	- roles are interchangeable with users
	- roles also have policy documents
	- roles can be assumed for a temporary time period
	- users and applications can have ability to assume a role
- trust relationships
	- use of roles for users to assume access to resources between accounts

Pro tips
- protect root at all costs
- explicit effect deny beats effect allow
	- deny supersedes allow at all levels
- use least privilege model
	- specify least resource and action needed to do a thing
	- minimize wild cards
- use aws policy simulator
	- policy builder and tester

Summary
- create users who use credentials that grant access based on their policy document
- create roles which can be assumed by entities within or across accounts with a trust relationship

Make dynamoDB IAM policy
- IAM console access management
	- groups, users, roles, and policies
- resource group add user
- dynamoDB user with access key and ID
- policy contains
	- service, action, resources, conditions
- associate policy with user
	- attach policy to add permissions

```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "DynamoReadWriteTransactionsTable".
			"Effect": "Allow",
			"Action": [
				"dynamodb:PutItem",
				"dynamdb:GetItem"
			],
			"Resource": "arn:aws:dynamodb:us-east-1:398447858632:table/Transactions"
		}
	]
}
```

