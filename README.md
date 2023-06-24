# terraform-aws-ecs-app-nlb

This terraform module is an AWS ECS Application Module that creates a Networking LoadBalance Application setup on ECS.

The following resources will be created:

 - Cloudwatch Metrics alarm - Provides a CloudWatch Metric Alarm resource.
 - IAM roles - The cloudwatch event needs an IAM Role to run the ECS task definition. A role is created and a policy will be granted via IAM policy.
 - IAM policy - Policy to be attached to the IAM Role. This policy will have a trust with the cloudwatch event service. And it will use the managed policy `AmazonEC2ContainerServiceEventsRole` created by AWS.
 - Security Groups for the ECS nodes
 - Simple Notification Service (SNS) topics - Alarm topics to create and alert on ECS service metrics. Leaving empty disables all alarms.
 - Auto Scaling
    - You can specify the max number of containers to scale with autoscaling. The default is 4
    - You can specify the nin number of containers to scale with autoscaling. The default is 1
    - Cooldown in seconds to wait between scale in events. The default is 300
    - Cooldown in seconds to wait between scale out events. The default is 300
 - Cloudwatch Log Groups
 - Network Load Balancer (NLB)
 - ECS task definition - A task definition is required to run Docker containers in Amazon ECS. Some of the parameters you can specify in a task definition include:
      - Image - Docker image to deploy
           - Default value = "dnxsolutions/nginx-hello:latest"
      - CPU - Hard limit of the CPU for the container
           -  Default Value = 0
      - Memory - Hard memory of the container
           -  Default Value = 512
      - Name - Name of the ECS Service
      - Set log configuration

 - ECS Task-scheduler activated by cloudwatch events

In addition you have the option to create or not :
 - Autoscaling
     - Enables or not autoscaling based on average CPU tracking
     - Target average CPU percentage to track for autoscaling
 - A Hostname to create DNS record for this app


# infra-test
