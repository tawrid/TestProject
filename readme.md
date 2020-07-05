# Processes to excute

In order to deploy the application following commands are required to be executed:


Pre-requisite:

You will have to setup the awsebcli before proceeding with the next steps.

Reference Link: https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html

Deployment Architecure: https://github.com/tawrid/TestProject/blob/master/Deployment_Architecture.png

First you will have to initiate Elastic BeanStalk (EB):

#eb init -p go <Application_Name> --profile <AWS profile name>


As next step you will have to follow the prompt to setup your local environment:

#eb init  


Afterward you will have to create the stack:

#eb create <Application_Name> --database --database.username <User_Name> --database.password <DB_Password> --database.engine <DB_Engine_Name> -db.i <DB_Instance_Type> --scale 1


Then we should be able to deploy the application:

#eb deploy


To destroy/uninstall the deployment execute:

#eb terminate

Limitations:

1. Access to the application may not be available due to security group restrictions. You will have to manually modifiy the instance related SecurityGroup configuraitons to allow your traffic.

2. Can use the EB provided FQDN or EC2 public IP to visit the application.
