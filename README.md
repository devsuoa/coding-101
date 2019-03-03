# coding-101
Library used for the DEVS coding 101 workshop. The library consists of two
parts. The `api` directory contains a REST API used to interact with AWS
services such as Comprehend and Rekognition. The `module` directory contains a
node module which acts as an SDK for the API.

## API
The API is hosted on AWS using the AWS Serverless Application Model (SAM) which
is a superset of CloudFormation.

### Dependencies
To build/run/deploy the API, the awscli and aws-sam-cli must first be
installled. Note that python 2.7, 3.6 or 3.7 must be installed as well as
Docker.

```bash
pip install --user --upgrade awscli
pip install --user --upgrade aws-sam-cli
```

### Local Testing
The API can be tested locally at `localhost:3000`. 

```bash
cd api
sam build
sam local start-api
```

### Deployment
The API can be deployed as follows.

```bash
cd api
sam build
sam package --template-file template.yaml \
--output-template-file packaged.yaml \
--s3-bucket YOUR-BUCKET-HERE
sam deploy --template-file packaged.yaml \
--stack-name STACK-NAME \
--capabilities CAPABILITY_NAMED_IAM
```

### Undeployment
Similarly, the API can be undeployed.

```bash
sam undeploy --stack-name STACK-NAME
```

## Module
The Node Module is published using npm.
