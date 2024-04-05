# css-cloudformation
Implementation of infrastructure as code in cloudformation.

## Layout Admin App

This CloudFormation template creates resources for an admin application layout, including a database, Cognito user pool, API Gateway, Step Functions state machine, and related configurations.

### Parameters

- **DBName**: Name of the database (default: mydatabase)
- **DBUsername**: Database username (default: admin)
- **DBPassword**: Database password (hidden)
- **CognitoUserPoolName**: Name of the Cognito user pool

### Resources

#### Cognito User Pool

Creates a Cognito user pool for user management.

#### API Gateway

Creates an API Gateway for RESTful API endpoints.

#### API Gateway Authorizer

Configures a Cognito user pool authorizer for API Gateway.

#### API Gateway Resource and Method

Adds a resource and method to the API Gateway, protected by the Cognito user pool authorizer.

#### Step Functions State Machine

Defines a basic Step Functions state machine (`StepFunctionSensors`) that returns "Infor Sensors".

#### RDS Database (Aurora Serverless)

Provisions an Aurora Serverless database with specified parameters.

### Outputs

- **DBEndpoint**: Database endpoint
- **CognitoUserPoolId**: ID of the Cognito user pool
- **ApiGatewayRestApiId**: ID of the API Gateway
- **HelloWorldStepFunctionArn**: ARN of the HelloWorld Step Functions state machine

This CloudFormation template creates a foundational infrastructure for an admin application, including authentication with Cognito, API Gateway endpoints, a serverless Aurora database, and a basic Step Functions state machine. Adjust parameters and resources as needed for your application requirements.

## Layout Portal Truck

This CloudFormation template creates resources for a truck portal, including a website hosted on S3, CloudFront distribution for the website, an API Gateway with a GET method backed by a Lambda function, a Cognito User Pool for user authentication, and related configurations.

### Parameters

- **DomainName**: Domain name for CloudFront.
- **ApiName**: Name for the API Gateway.
- **FunctionArn**: ARN of the Lambda function for the GET method.
- **CognitoUserPoolName**: Name of the user pool for Cognito.

### Resources

#### S3 Bucket

Creates an S3 bucket to host the web application.

#### CloudFront Distribution

Configures a CloudFront distribution to serve the website from the S3 bucket.

#### API Gateway

Creates an API Gateway with a resource and a GET method protected by a Cognito authorizer.

#### Lambda Function

The Lambda function backs the GET method of the API Gateway.

#### Cognito User Pool

Sets up a Cognito User Pool for user authentication.

#### Cognito User Pool Client

Creates a client for the Cognito User Pool for the application.

#### Cognito User Pool Domain

Assigns a custom domain to the Cognito User Pool.

#### WAFv2 WebACL and RuleGroup

Configures a Web Application Firewall (WAF) for CloudFront and the API Gateway.

#### DynamoDB Table

Creates a DynamoDB table with PK and SK keys for storing data.

### Outputs

- **CloudFrontDomainName**: Domain name of the CloudFront distribution.
- **ApiGatewayInvokeURL**: Invocation URL of the API Gateway.
- **CognitoUserPoolId**: ID of the Cognito User Pool.
- **CognitoUserPoolClientId**: ID of the Cognito User Pool client.

This CloudFormation template deploys a basic infrastructure for a truck portal, including a website, API Gateway protected by Cognito, Lambda function, and security configurations with WAFv2. Adjust the parameters and resources according to your application requirements.

## Real Time Layout

This CloudFormation template provisions resources for a real-time data processing setup, including AWS IoT Greengrass, Kinesis Data Streams, Kinesis Video Streams, Amazon QuickSight for analytics, and related configurations.

### Parameters

- **GreengrassGroupName**: Name of the AWS IoT Greengrass group.
- **KinesisDataStreamName**: Name of the Kinesis Data Stream.
- **KinesisVideoStreamBucketName**: Name of the bucket for Kinesis Video Stream.
- **CertificateSigningRequest**: Certificate signing request for x.509 certificate.
- **QuickSightAnalysisName**: Name of the QuickSight analysis.
- **QuickSightDataSetArn**: ARN of the QuickSight dataset.
- **QuickSightDashboardName**: Name of the QuickSight dashboard.

### Resources

#### IoT Components

- **IoTThingDefinition**: Defines IoT things for location, speed, temperature, and alert sensors.
- **IoTConnectorDefinition**: Defines the IoT connector.
- **IoTGroup**: Creates an AWS IoT Greengrass group.
- **IoTCoreDefinition**: Defines the core device for AWS IoT Greengrass.
- **CoreThing**: Creates a core IoT device.
- **CoreCertificate**: Generates an IoT certificate for the core device.
- **CoreThingRule**: Defines an IoT rule for the core device.
- **IoTRule**: Another IoT rule for general IoT actions.

#### Stream Kinesis

- **KinesisDataStream**: Creates a Kinesis Data Stream.
- **KinesisAnalyticsApplication**: Sets up a Kinesis Analytics application to process streaming data.
- **KinesisVideoStream**: Creates a Kinesis Video Stream.
- **FirehoseDeliveryStream**: Configures a Kinesis Firehose delivery stream.

#### S3 Buckets

- **KinesisVideoStreamBucket**: Creates an S3 bucket for Kinesis Video Stream.
- **KinesisFirehoseStreamBucket**: Creates an S3 bucket for Kinesis Firehose.

#### SNS Topic

- **SNSTopic**: Creates an SNS topic for notifications.

#### QuickSight Analytics

- **QuickSightAnalysis**: Configures an AWS QuickSight analysis.
- **QuickSightDashboard**: Sets up an AWS QuickSight dashboard.

#### IAM Roles and Policies

- **KinesisAnalyticsServiceRole**: IAM role for Kinesis Analytics.
- **KinesisVideoStreamIAMRole**: IAM role for Kinesis Video Stream.
- **FirehoseRole**: IAM role for Kinesis Firehose.

### Outputs

- **QuickSightDashboardURL**: URL to access the AWS QuickSight dashboard.

This CloudFormation template orchestrates the setup of real-time data processing components using AWS services such as IoT Greengrass, Kinesis Data Streams, and QuickSight for analytics. Adjust the parameters and resources according to your use case and requirements.
