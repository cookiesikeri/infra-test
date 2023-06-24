# terraform-aws-ecs-app-nlb by ikeri ebenezer

This terraform module is an AWS ECS Application Module that creates a Networking LoadBalance Application setup on ECS.

The following resources will be created:

 - Cloudwatch Metrics alarm - Provides a CloudWatch Metric Alarm resource.
 - IAM roles - The cloudwatch event needs an IAM Role to run the ECS task definition. A role is created and a policy will be granted via IAM policy.
 - IAM policy - Policy to be attached to the IAM Role. This policy will have a trust with the cloudwatch event service. And it will use the managed policy `AmazonEC2ContainerServiceEventsRole` created by AWS.
 - Security Groups for the ECS nodes
 - Simple Notification Service (SNS) topics - Alarm topics to create and alert on ECS service metrics. Leaving empty disables all alarms.
 - Auto Scaling
 - Cloudwatch Log Groups
 - Network Load Balancer (NLB)
 - ECS task definition - A task definition is required to run Docker containers in Amazon ECS.
 - ECS Task-scheduler activated by cloudwatch events

In addition i added some optional modules:
 - Autoscaling
     - Enables or not autoscaling based on average CPU tracking
     - Target average CPU percentage to track for autoscaling
 - A Hostname to create DNS record for this app.


how to spin up infra:
1. terraform init (to initialize terraform)
2. terraform plan: to see the resources that are going to be provisioned (or changed)
3. terraform apply:  to deploy them

 please feel free to reach out to me for any question thank you. ...