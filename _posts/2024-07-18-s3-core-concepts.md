---
layout: post
s3-docs: https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html
s3-yt: https://youtu.be/tfU0JEZjcsg?si=UwQK91ctuBVz-EYU

---

Simple storage service (S3) was the first AWS service launched in 2006. S3 focuses on general object storage in "the cloud". General objects include files, source code, media, and data. S3 is generally cheap, highly available, highly durable, and it integrates with many AWS services. S3 is useful for website hosting, database backups, data processing, and storing software artifacts. Notes below cover S3 core concepts. 

[S3 AWS documentation]({{page.s3-docs}})

[Short video on S3 basics]({{page.s3-yt}})

Core concepts
- objects in buckets with globally unique names
- buckets have a 5TB maximum size
- bucket is a general purpose file system with flexible organization
- objects are stored in buckets in the file system
- create bucket and structure, put objects in bucket, retrieve objects from bucket
- retrieve objects via http url, only public bucket, private by default
- retrieve object via boto3 s3client.get_object()
- retrieve object via aws console
- control bucket access and operations with bucket policy or IAM policy

Storage classes
- buckets and objects can have different storage classes
- storage classes have decreased cost but decreased performance
- standard, intelligent, infrequent access, glacier
- different pricing, latency, and availability
- hot data, infrequent access, and cold data cycle through storage classes
- life cycle rules automate storage tier cycling

Security
- misconfigured S3 Bukets can easily leak data
- public access is blocked by default
- objects are encrypted in transit and at rest, has to be configured
- access and resource controls with AWS IAM
- logging and alarms integrate with cloudwatch, has to be configured
- assume AWS cloud infrastructure security

S3 in action
- data ingestion pipeline
	- API based stock data stream
    - kinesis firehouse batching of independent events
    - deliver batches to s3
    - batch event triggers lambda
    - batch object is used by lambda
- S3 events for object creation, deletion, modification
	- trigger event to invoke lambda, pass bucket name and object key
	- pull object, do operation, return object to bucket, or do something else
- s3 and lambda is a useful combination
- analytics and dashboarding
	- athena analytics service on bucket contents
	- bucket objects have to follow a scheme
	- pay per use, no database provisioning
	- athena, s3, quicksight
- event driven architectures
	- image uploading pipeline
	- customer, s3, lambda, appsync
	- s3 to lambda put notification, run process on lambda
	- notify customer download is ready with pub/sub model

Pricing
- dependent on storage classes
- three main factors
	- stored object size and number
	- accessing objects over network with GET and POST
	- transferring objects between buckets and services
- 100gb storage, 10K PUT, 10 Read
	- standard 6.76 / month
	- infrequent access 6.27 / month
	- glacier 6.64 / month
- free tier
	- 5gb, 20k get, 2K put
	- 12 month max

