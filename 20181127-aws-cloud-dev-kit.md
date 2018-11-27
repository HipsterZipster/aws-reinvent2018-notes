20181127
DEV372
Infrastructure is Code with the AWS Cloud Development Kit

Elad Ben-Israel
Jason Fulghum

# Infra Management Journey

From low level to higher level

## Manual

- Easy to get started
- Not reproducible
- Error-prone
- Time consuming

## Scripted

- What happens if an api call fails?
- How do I make updates?
- How do I know a resource is ready?
- How do I roll back?

## Declarative - resource provisoning engines

- easy to automate
- reproducible
- configuration syntax
- no abstraction, lots of details

## DOMs

- real code
  (if statement, for loops, ide benefits)
- desired state
- abstraction is not built-in (ex: 218 lines of troposphere for a vpc)

# Componentized - AWS CDK

- SDK for defining your infra and your cloud resources

## Demo -goals

send message to sqs queue -> event source aws lambda -> cloudwatch logs

## Demo - Writing constructs

- thinking in constructs
- permissions - grant apis
- wiring runtime configuration

AWS built a "Cloud Development Kit", a series of libraries that allow you to generate infrastructure and the like using normal languages instead of using declarative yaml etc. Well they built v1 with java, typescript
