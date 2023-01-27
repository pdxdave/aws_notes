# Elastic Beanstalk

## What it is
It's a Platform as a Service.  The infrastruction is already built and no user maitenance is required.    
It's the Heroku for AWS.    
Not ideal for enterprise companies as all of the customization is out of your hands.
It's built on CloudFormation. This is a service that sets everything up in the background for you.    
You pick the resources you want, and AWS sets everything up in the background. These would include
* Elastic Load Balancer
* Autoscaling Groups
* RDA Database
* EC2 Instance preconfiged platforms (Go, .Net, Node.js, Ruby, PHP, etc)
* Monitoring (CloudWatch, SNS)
* Security (Rotates passwords for RDS)
* Dockerized environments

## Supported languages
* Ruby > Rails
* Python > Django
* PHP > Laravel
* Tomcat > Spring
* NodeJS > ExpressJS

## Web vs Work Environment
![web_v_workenvironment](/assets/img1.png)
![ec2_instance](/assets/ec2.png) EC2 instances (1 or more)     
![asg](/assets/asg.png) ASG is an Auto Scaling Group.     
![elastic_load_balancer](/assets/elb.png) Elastic load balancer (1 or more)       

