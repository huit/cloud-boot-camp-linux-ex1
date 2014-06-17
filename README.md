Cloud-Boot-Camp-exercise 1 README File
=========================
Exercise 1 Requirements: https://github.com/huit/cloud-boot-camp/wiki/Deploying-a-Fault-Tolerant-LAMP-based-Service

Original CloudFormations Template: https://s3.amazonaws.com/cloudformation-templates-us-east-1/Drupal_Multi_AZ.template

Exercise 1 Description: This exercise models a LAMP based website for which most of the traffic is read-only. By exploiting the lack of shared session between requests, the read-only view of the site can be scaled horizontally

Tools Needed: https://github.com/huit/cloud-boot-camp#tools

AWS Command to Run:
=========================

Macintosh Instructions:

1.  Launch the Terminal Window on your Macintosh

2.  Type the following command:

```
aws cloudformation create-stack \
  --capabilities CAPABILITY_IAM \
  --stack-name HPACDrupalStackWebInfrastructure \
  --template-url https://s3.amazonaws.com/hpacdrupalstack-s3bucket-12npg1o22mj36/Drupal_Multi_AZ.template \
  --parameters ParameterKey=KeyName,ParameterValue=HPACDrupalKeyPair
```
NOTE: aws command above is using the cloudformation template located in an S3 bucket on Amazon at the location specified.  All future updates to the template should be uploaded to this location and overwritten to the file.

3. Login to https://cloudhacks.signin.aws.amazon.com/console

4. Open the AWS Console

5. Enter your Username, Password and MFA Token.

HPAC Drupal Infrastructure Components:
=========================

The Drupal_Multi_AZ.template CloudFormation template will create the following instances:

   - 1 Load Balancer
   - 2 Web Server Instances in the us-east-1d Availability Zone
   - 1 Web Server Instance in the us-east-1a Availability Zone
   - 1 RDS Instance PRIMARY us-east-1d
   - 1 RDS Instance SECONDARY us-east-1a
   
Demonstration of Exercise 1
=========================

1. Show documentation of original CloudFormation Template and Changes
2. Show S3 Bucket that contains Updated CloudFormatin Template
   - hpacdrupalstack-s3bucket-12npg1o22mj36
3. Show Single Command to initiate HPAC Drupal Infrastructure Build

Demonstration of Resiliency
=========================

Demonstrate that the site remains up and responsive to the following failures:
 * Failure of the master RDS instance
 * Failure of an individual instance
   - Demonstrate Rebuild of Instance using following command:
   - Change Template 
      - What if it is 1, what if it is 3?
   - aws cloudformation update-stack --capabilities CAPABILITY_IAM --stack-name HPACDrupalStackWebInfrastructure --template-url https://s3.amazonaws.com/hpacdrupalstack-s3bucket-12npg1o22mj36/Drupal_Multi_AZ.template --parameters ParameterKey=KeyName,ParameterValue=HPACDrupalKeyPair

 * Failure of ALL object in a given availability zone.
=======
Exercise 1:

  - Location of Requirements:  https://github.com/huit/cloud-boot-camp/wiki/Deploying-a-Fault-Tolerant-LAMP-based-Service
  - Base CloudFormation Template File: https://s3.amazonaws.com/cloudformation-templates-us-east-1/Drupal_Multi_AZ.template

Next Steps for Exercise 1

- Logging - Splunk
- Monitoring - Nagios
- Add an Admin Node
- Clean-up
- Route 53
- Import Data for Drupal Website
- Fix the name of instances
