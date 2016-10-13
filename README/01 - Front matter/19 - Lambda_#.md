#Lambda
------

### Lambda Basics

-	📒 [Homepage](https://aws.amazon.com/lambda/) ∙ [Developer guide](http://docs.aws.amazon.com/lambda/latest/dg/) ∙ [FAQ](https://aws.amazon.com/lambda/faqs/) ∙ [Pricing](https://aws.amazon.com/lambda/pricing/)
-	**Lambda** is a relatively new service (launched at end of 2014) that offers a different type of compute abstraction: A user-defined function that can perform a small operation, where AWS manages provisioning and scheduling how it is run.

### Lambda Tips

-	**What does “serverless” mean?** This idea of using Lambda for application logic has grown to be called **serverless** since you don't explicitly manage any server instances, as you would with EC2. This term is a bit confusing since the functions themselves do of course run on servers managed by AWS. [Serverless, Inc.](http://serverless.com/) also uses this word for the name of their company and [their own open source framework](https://github.com/serverless/serverless), but the term is usually meant more generally.
-	The release of Lambda and [API Gateway](#api-gateway) in 2015 triggered a startlingly rapid adoption in 2016, with many people writing about [serverless architectures](http://martinfowler.com/articles/serverless.html) in which many applications traditionally solved by managing EC2 servers can be built without explicitly managing servers at all.
-	**Frameworks:** [Several frameworks](https://github.com/anaibol/awesome-serverless#frameworks) for building and managing serverless deployment are emerging.
-	The [Awesome Serverless](https://github.com/anaibol/awesome-serverless) list gives a good set of examples of the relatively new set of tools and frameworks around Lambda.
-	The [**Serverless framework**](https://github.com/serverless/serverless) is a leading new approach designed to help group and manage Lambda functions. It’s approaching version 1 as of August 2016) and is popular among a small number of users.

### Lambda Alternatives and Lock-in

-	🚪Other clouds offer similar services with different names, including [Google Cloud Functions](https://cloud.google.com/functions/), [Azure Functions](https://azure.microsoft.com/en-us/services/functions/), and [IBM OpenWhisk](http://www.ibm.com/cloud-computing/bluemix/openwhisk/).

### Lambda Gotchas and Limitations

-	🔸Lambda is a new technology. As of mid 2016, only a few companies are using it for large-scale production applications.
-	🔸Managing lots of Lambda functions is a workflow challenge, and tooling to manage Lambda deployments is still immature.
-	🔸AWS’ official workflow around managing function [versioning and aliases](https://docs.aws.amazon.com/lambda/latest/dg/versioning-aliases.html) is painful.

🚧 [*Please help expand this incomplete section.*](CONTRIBUTING.md)

