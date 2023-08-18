# Cloud Monitoring

## Cloudwatch Metrics
- Metric is variable to monitor (CPU utilization, Network Latency, Billing)
- Metrics can be in intervals so that they are more up to date
- S3 Buckets: BucketSizeBytes, Number of Objects, All Requests
## Cloudwatch Alarms
- Once a metric goes over a certain threshold we can trigger an alert.
- Ex: If EC2 CPU utilization is over 90% send us an email
## Cloudwatch Logs
- Collects log files from resources and allows use to monitor the application in real time
- By default EC2 instances will not send any logs to CloudWatch
- CloudWatch agent will need to be installed on EC2 to be able to push the log file that we want
## Amazon EventBridge
- Schedule Cron Jobs
- In event bridge you can create a rule that will trigger a lambda script every 1 hour
- You can create event rules to react to a service doing something (someone logging into root user event)
- Create all types of events using this resource!
- There are Default Event Buses (AWS Native), Partner Event Bus (DataDog, ZenDesk and more AWS partners) and Custom Event Bus (Custom Apps).
## Cloudtrail
- Provides governance, compliance and audit for AWS accounts
- CloudTrail is enabled by default
- Any service activity will be logged in cloudtrail (AWS, Console, SDK, CLI)
- You can put logs from CloudTrail in to Cloudwatch Logs or S3 for long term retention
- if a resource is deleted in AWS look at CloudTrail first!
## AWS X-Ray
X-Ray provides a visual analysis of our applications and we can see where it is failing, where something went wrong and etc.
- Good for troubleshooting performance, understanding dependencies in microservice architecture, review request behavior, find errors and etc.
## AWS Code Guru
- Machine Learning powered service.
- Code Guru reviewer will do code reviews with static code analysis (SAST).
- CodeGuru Profiler will recommend things for your applications about performance in production.
- Integrates with GitHub, Bitbucket and AWS CodeCommit
## AWS Health Dashboard
AWS Service History:
- Shows all regions and all services health
- Shows historial information for each day

Your Account:
- Alerts and remediation alerts for when AWS is experiencing events.
- Displays health and relevant events for services that you utilize