Repo Name
=========
aws-lambda-transcribe-audio

Description
---------------
AWS Lambda script to transcribe (speech to text) an audio file uploaded to an S3 bucket and put the finished transcription in another bucket. Uses Python (tested with 3.7), Amazon's boto3 SDK, Amazon Transcribe, and a couple of triggers.

Prerequisites
---------------
* The [boto3 SDK](https://aws.amazon.com/sdk-for-python/).
* Ensure that the IAM Role attached to the Lambda function has policies for CloudWatch and [Amazon Transcribe](https://docs.aws.amazon.com/transcribe/index.html) as well as write access to the destination S3 bucket. CloudWatchLogsFullAccess, AmazonTranscribeFullAccess, and the s3.PutObject permission will certainly work.
* Ensure that an audio file upload to your origin S3 bucket triggers the Lambda function.
* Ensure that DEST_BUCKET in your Lambda function specifies your destination bucket.

### To set up boto3 for development (Amazon Linux and similar):
```
sudo yum install -y python3 python3-pip python3-setuptools
pip3 install boto3 --user
aws configure [enter your AWS access key and secret key]

python3
>>> import boto3
>>> ec2 = boto3.client('ec2')
>>> response = ec2.run_instances(ImageId='ami-00dc79254d0461090',InstanceType='t2.micro',KeyName='MY KEY',MinCount=1,MaxCount=1)
```
