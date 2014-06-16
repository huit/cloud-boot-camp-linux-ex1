Cloud-Boot-Camp-exercise 1 README File
=========================

Exercise 1 Requirements: https://github.com/huit/cloud-boot-camp/wiki/Deploying-a-Fault-Tolerant-LAMP-based-Service

Original CloudFormations Template: https://s3.amazonaws.com/cloudformation-templates-us-east-1/Drupal_Multi_AZ.template

Exercise 1 Description: This exercise models a LAMP based website for which most of the traffic is read-only. By exploiting the lack of shared session between requests, the read-only view of the site can be scaled horizontally

Tools Needed: https://github.com/huit/cloud-boot-camp#tools

AWS Command to Run:  

aws cloudformation create-stack --capabilities CAPABILITY_IAM --stack-name HPACDrupalStack --template-body file://////Users/spm888/git/cloud-boot-camp-linux-ex1/Drupal_Multi_AZ.template --parameters ParameterKey=KeyName,ParameterValue=HPACDrupalKeyPair
