---
layout: post
s3-docs: https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html 
iam-docs: https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html 
s3-iam-yt: https://www.youtube.com/watch?v=gWAwqY76JQs

---

IAM and S3 bucket policies offer tools for controlling actions against S3 buckets and objects stored within. In practice both methods function similiarly but differ in the way they are attached to users and resources. Below are general notes on IAM and S3 bucket policies.

[S3 bucket policy documentaion]({{page.s3-docs}})

[IAM documentation]({{page.iam-docs}})

[Short youtube video comparing S3 and IAM policies]({{page.s3-iam-yt}})

IAM recap
- identity and access management
- define polices on resources
	- statement, effect, action, and resource
	- actions allowed/denied
	- json
- resources are entities
- policies used to define access to resources
- policies are attached to
	- users, roles, and groups
- implicit and explicit deny
- deny beats allow

S3 bucket policies
- policies attached to s3 buckets
	- similiar to IAM policy
	- principal key
	- json 
- policy permissions applied to a principal
	- person or application
- policy is attached to bucket
	- opposed to IAM which is attached to user, role, or group

Good to know
- IAM and resource policies can be used to together
	- IAM for global permissions
	- resources policy for specific permissions
	- specific resource will trump global IAM
- s3 bucket policies are useful for cross account access management
	- larger policy size to support cross account management
