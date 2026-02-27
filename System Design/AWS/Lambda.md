Lambda are serverless, event-driven Function as a Service ([[FaaS (Functions as a Service)]]), Lambda functions enable developers to run code without provisioning servers. 

It executes code in response to events issued from other services.

Lambda uses small and fast virtual machines that can start up within seconds and run your code.

Lambda functions should be relatively small and short, there is a disk and memory limits allocated to each instance and a timeout of 15 minutes.

Lambdas are stateless, for heavy and long processing different solutions should be considered, like an EC2 instance. 

### Common use cases:

#### Resources usage
A User uploads a file to an S3 bucket, the upload triggers a Lambda function, which processes the file (such as compression, thumbnail generation).

#### Backups
You can schedule backup tasks using Lambda

#### Log Analysis
You can schedule log analysis to look for specific log types or errors and act upon them.