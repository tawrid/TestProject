# Introduction

This project will deploy:
1. A Go application 
2. An application, which will use RDS as DB
3. An application, which will have high availability
4. An application, which will have auto-scaling enabled

# Processes to excute

In order to deploy the application following commands are required to be executed:


## Pre-requisite

You will have to setup the following items before proceeding with the next steps:
1. awscli 
2. awsebcli 
3. eb init to setup the keys and environemnt etc. for aws access

## Reference Link 
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html

## Deployment Architecure 
https://github.com/tawrid/TestProject/blob/master/Deployment_Architecture.png

## Steps

1. First you will have to initiate Elastic BeanStalk (EB):

```eb init -p go <Application_Name> --profile <AWS profile name>```

2. Afterward you will have to create the stack with provided DB credentials:

```eb create <Application_Name> --database --database.username <User_Name> --database.password <DB_Password> --database.engine postgres -db.i <DB_Instance_Type> --scale 1```

3. Then we should be able to deploy the application:

```eb deploy```

4. To open the application in your browser run 

```eb open```

4. To destroy/uninstall the deployment execute:

```eb terminate```

## Limitations:
1. Access to the application may not be available due to security group restrictions. You will have to manually modifiy the instance related SecurityGroup configuraitons to allow your traffic.

2. Use the EB provided FQDN or EC2 public IP to visit the application.
