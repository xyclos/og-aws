#Auto Scaling
------------

### Auto Scaling Basics

-	📒 [Homepage](https://aws.amazon.com/autoscaling/) ∙ [User guide](http://docs.aws.amazon.com/autoscaling/latest/userguide/) ∙ [FAQ](https://aws.amazon.com/ec2/faqs/#Auto_Scaling) ∙ [Pricing](https://aws.amazon.com/autoscaling/pricing/) at no additional charge
-	[**Auto Scaling Groups (ASGs)**](https://aws.amazon.com/autoscaling/) are used to control the number of instances in a service, reducing manual effort to provision or deprovision EC2 instances.
-	They can be configured, through [Scaling Policies](http://docs.aws.amazon.com/autoscaling/latest/userguide/policy_creating.html),” to automatically increase or decrease instance counts based on metrics like CPU utilization, or based on a schedule.
-	There are three common ways of using ASGs - dynamic (automatically adjust instance count based on metrics for things like CPU utilization), static (maintain a specific instance count at all times), scheduled (maintain different instance counts at different times of day or on days of the week).
-	💸ASGs [have no additional charge](https://aws.amazon.com/autoscaling/pricing/) themselves; you pay for underlying EC2 and CloudWatch services.

### Auto Scaling Tips

-	💸 Better matching your cluster size to your current resource requirements through use of ASGs can result in significant cost savings for many types of workloads.
-	Pairing ASGs with CLBs is a common pattern used to deal with changes in the amount of traffic a service receives.
-	Dynamic Auto Scaling is easiest to use with stateless, horizontally scalable services.
-	Even if you are not using ASGs to dynamically increase or decrease instance counts, you should seriously consider maintaining all instances inside of ASGs – given a target instance count, the ASG will work to ensure that number of instances running is equal to that target, replacing instances for you if they die or are marked as being unhealthy. This results in consistent capacity and better stability for your service.
-	Autoscalers can be [configured to terminate](http://docs.aws.amazon.com/autoscaling/latest/userguide/healthcheck.html) instances that a CLB or ALB has marked as being unhealthy.

### Auto Scaling Gotchas and Limitations

-	By default, ASGs will kill instances that the EC2 instance manager considers to be unresponsive. It is possible for instances whose CPU is completely saturated for minutes at a time to appear to be unresponsive, causing an ASG with the default '[ReplaceUnhealthy](http://docs.aws.amazon.com/autoscaling/latest/userguide/as-suspend-resume-processes.html#process-types)' setting turned on to replace them. When instances that are managed by ASGs are expected to consistently run with very high CPU, consider deactivating this setting. If you do so, however, detecting and killing unhealthy nodes will become your responsibility.

