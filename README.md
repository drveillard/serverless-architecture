# Serverless Architecture

## What is serverless?
Serverless allows you to build and run applications and services without thinking about servers. It eliminates infrastructure management tasks such as server or cluster provisioning, patching, operating system maintenance, and capacity provisioning. You can build them for nearly any type of application or backend service, and everything required to run and scale your application with high availability is handled for you.


![serverless](https://github.com/drveillard/serverless-architecture/blob/main/img/Cloud-Computing.png)

 - Serverless applications are event-driven and loosely coupled via technology-agnostic APIs or messaging. 
 - Event-driven code is executed in response to an event, such as a change in state or an endpoint request. 
 - Event-driven architectures decouple code from state. Integration between loosely couple components is usually done asynchronously, with messaging.


## Why use serverless?
- **No server management:** - There is no need to provision or maintain any servers. There is no software or runtime to install, maintain, or administer.

- **Flexible scaling:** - Your application can be scaled automatically or by adjusting its capacity through toggling the units of consumption (e.g. throughput, memory) rather than units of individual servers.

- **Pay for value:** - Pay for consistent throughput or execution duration rather than by server unit.

- **Automated high availability:** - Serverless provides built-in availability and fault tolerance. You don't need to architect for these capabilities since the services running the application provide them by default.


## Table of Contents
 - [Intro AWS Serverless Architecture](#intro-to-aws-serverless-architectures)
 - [100 % Serveless Architecture on AWS](#)




## AWS Serverless Architecture


### Intro to AWS Serverless Architecture
[Serverless architecture](https://dev.to/dev0928/intro-to-web-app-using-aws-serverless-architecture-f91) comprises a group of technologies working together as a single unit to deliver a solution. In this write-up, let’s review the involved technologies along with their high level purpose to build a web application.


![architecture](https://github.com/drveillard/serverless-architecture/blob/main/img/AWS-serverless.png)

### Backend
Backend is a stand-alone service comprising three main components - Data store, Lambda functions used as a compute service and API Gateway acting as a main backend interface.

#### Data Store / Database
Aurora Serverless (PostgreSQL) is one of the options. There are few other serverless database options available to choose from. Data store choice purely depends on the type of data stored within the application.

#### Lambda Functions
Lambda functions with Python could be used on the backend. AWS Lambda supports many other options such as Node.js, Java, .NET Core, PHP.

#### API Gateway
API Gateway serves as a gatekeeper to the backend service. API endpoints can be secured and served through the API Gateway. API Gateway leverages lambda functions to perform necessary data processing to serve requests made to the API endpoint. Frontend applications or any other service requiring data can call these API endpoints with required security token to obtain necessary data.

### Frontend
Frontend framework such as Angular, Vue, React or any other framework could be used to build the frontend website. During deployment, front-end code is built and deployed to AWS CloudFront CDN and served to the end users’ browsers upon request.

### Security
AWS Cognito is an Amazon authentication and authorization service. This service also has support for SAML / OAuth2 / Open ID authentication through major Identify providers such as Facebook, Google, Okta.

Supporting Services
Besides above mentioned core services, there are many other supporting services involved in the serverless application architecture. Let’s review the purpose of these supporting services.

Serverless Framework
Serverless Framework helps develop and deploy serverless applications along with the required infrastructure resources they require. It's a CLI that offers structure, automation and best practices out-of-the-box and helps build sophisticated, event-driven, serverless architecture applications. Framework itself is built with Node.js but it can support multiple languages (Node.js, Python, Java, and more). This framework is cloud-agnostic meaning one can use this framework to develop serverless applications for any cloud provider.

AWS Serverless Application Model is an alternative option to serverless framework but it is specific to AWS.

AWS CloudFormation
AWS CloudFormation gives an easy way to model a collection of related AWS resources, provision them quickly and consistently across different environments, and manage them throughout their life cycles, by treating infrastructure as code. Serverless framework’s configuration files describe all of the services that need to be provisioned for a given application.

AWS S3
Simple Storage Service(S3) can be used as an intermediate storage for transferring and processing data from external systems. S3 can also be used for storing artifacts during the build and deployment process.

IAM
Identity and Access Management Service is one of the important services in this solution. This service is mainly used for providing granular access permissions among various services used within the AWS serverless environment.

Route 53
This service is used for domain registration so deployed applications could be accessed using a user-friendly URL.

AWS CloudWatch
AWS CloudWatch is a logging service used by other services to log messages within the serverless solution. Messages logged in the service can be used for setting up alerts in case there are errors/issues within the application.

Source Control
AWS CodeCommit is AWS provided solution for source control. Other third party source control solutions such as Github can also be used for source code management.

Code Pipeline
This AWS solution enables automation of continuous build and deployment of applications.

Amazon SNS
Simple Notification Service used for event messaging. Events could be notified to multiple interested systems enabling microservices / distributed processing.

Amazon SQS
Simple Queue Service is a messaging service used for processing events sequentially. This service can scale well and also has facilities for guaranteed delivery of sequenced messages.

AWS Systems Manager
Systems Manager Parameter Store is used for application’s configuration and secrets management.

VPC
All of the services configured for the serverless solution would be deployed within the application’s secure Virtual Private Cloud environment. VPC should be configured properly to avoid security holes.

Benefits
Here are some of the benefits of using serverless architecture:

This architecture scales well from few users to thousands of concurrent users.
As there are no dedicated hardware resources provisioned as part of this solution, there is no infrastructure cost around server maintenance and upgrades.
Also, the services involved in this solution are charged based on usage. This solution could be cost effective if configured properly.

