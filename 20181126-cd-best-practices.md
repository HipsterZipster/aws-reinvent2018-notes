advacned continuous deliveyr best practices
DEV317-R

Curtis Rissi
Felipe

What you'll learn

Some of the continuous deploy best practices of Amazon

Continuous integration
Continuous delivery = manual approval
Continuous deployment = no manual approval

# Best continuous delivery best practices

- versioned source
- automated build
- automated deployments
- deploy to > one instance
- unit tetss
- integration tests
- continuous delivery
- operations dashboard

# Tools used in this talk

- Monitoring - AWS CloudWatch
- software dev - amazon SNS
- aws lambda
- continuous delivery - CodeDeploy
- continuous deploy - CodeDeploy

# Pipelines

- Made up of stages, stage has an action
- each stage has a transition which stages to go next
- Release and Deploy process - starting point
- To Dive Deeper with containers - DEV309-R - CI/CD for Serveless and containerized applications

## Automated Pipeline

- Defined as code
- Checked in a version control system like AWS CodeCommit
- Able to allow for extnsibility throughother aws services or thiurd party tools
- Able to prvoide fAST feedback on the success and failure of pipeline executions

Opportunity for automation

- ci processes - buuld integratipon tests, ui testing and more
  health checks
  applicatoin test
  synthetic user tests and application performancemonitoring
- Notifications and alerts
  - AWS cloudwatch alearms and third-party tools such as Splunk and Daddog
- Amazon sns, slack, pagerduty, and more

# Manage Deployment aHealth

- Builds on top of foundation of automation
- Purpose built to veify that a service is working
- Rolling deployments - Use elastic load balancing

## Add safety to rolling deployments

- Validate each host's health
- Working tests raises more issues
- Step 2 - uyse minimum health hosts MHH 70% - 10 hosts
- Rollback when deployment fails - if we dont meet the MHH rate

## Step 2 - Blue/Green Deploys

## Step 3 - Segmenting Deploys

- Lower deployment risk by segmenting
- Minimize the impact of deployment failures
- Potentially catch issues before real users do
- Enables you to roll back more quickly, with less impact

## Segemention overview

1. break prod up into multiple segments

- typical segment types

3. deploy to a segemnt

- use deployments groups per segement using tags or auto scaling groups (minimum should be 3 AZs)
  = deploy to smallest segement
  - post deploy tests
    -deploy to on availability zone
  - post deploy tests

5. test a segement after a deploymment

- The deploy is vaslid if the test has gathered enough data to gain confidence
- cloudwatch metrics
- no service alarms have been fired
  - cloudwatch alarms
- the test has not timed out
- code
- add segement terts to your pipeline
- extend them with test actions
- lambda invoke actions
- custom actions
- approval actions (has longer than a 1 hour timeout)

- If approvals are required:
- use SNS to start an automated approval check
- Create a post deployment test
- validate canary for approval
- publish to a sns topic
  -lambda function -registerDeployTest()
- amazon dynamodb
- lambda functopn evaluateDeploy() which checks usage, time, etc.
- evaluateDeploy() polls every minute for updates

7. repeat 2 and 3 until done
8.

### Canary Deployments are different

- all production hosts
- participoages in serving production traffic
- configered as a productoin instance
- participates in production metrics stream

canary hosts

- has its own metrics stream
- canary validates use the canary metrics stream

Summary: Segment Production

- segement production to reduce impact of a bad changes
  minim seg

- region
- canary deployment per region

# Cross-Region Deployments

- New as of November 2018
- Allows you to deploy to multiple regions from a single pipeline
- Enables you to acheive lower latency and greater availability

## Step 5: Implement Pipeline Governance

- Block non-compliant pipeline
- intrdocuign changes or even new pipelines can cause serious problems
- leverage aws config to ensure pipeline compliance
- Alert when pipelines are not configured up to company best praftices
- Building a pipeline action that checks health of the pipeline it's running on
- Provide developers a best practices pipeline to start from with AWS cloudformation templates

- Release and Deploy: Gates
- AWS CodeDeploy

### Code is available online

### Related
