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

