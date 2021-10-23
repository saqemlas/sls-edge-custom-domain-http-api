# Edge Optimized Custom Domain Http Api Gateway

## Info 

This handles deployment for a http api gateway with an integrated lambda, a cloudfront distribution, and hosted zone A record. 

Http Apis are designed for low-latency and cost-effective integrations, some benefits included in this deploment are:
- support catch-all routing (which is not possible with Rest Apis)
- global rules for CORS headers
- trigger AWS Lambda

For Edge Optimized Apis, the default hostname of an API Gateway that is deployed to the specified Region while using a CloudFront distribution to facilitate client access typically from across AWS Regions. API requests are routed to the nearest CloudFront Point of Presence (POP), which typically improves connection time for geographically diverse clients.

Currently, only Rest Api Gateways support edge optimization, whereby an AWS-Managed cloudfront distribution is deployed to improve client connection time. [See Here](https://aws.amazon.com/premiumsupport/knowledge-center/api-gateway-cloudfront-distribution/) As a workaround, this deployment includes a hosted zone a record to create the custom domain targeting the cloudfront distribution which is targeting the api endpoint using a custom origin.

For more information...
- [Serverless Framework: Http Support](https://www.serverless.com/blog/aws-http-api-support)
- [Serverless Framework: Http Lambda Events](https://www.serverless.com/framework/docs/providers/aws/events/http-api)
- [AWS Documentation: Http vs Rest](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-vs-rest.html)
- [AWS Documentation: Edge Optimized Api Endpoint](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-basic-concept.html#apigateway-definition-edge-optimized-api-endpoint)
- [AWS Documentation: Api Gateway Cloudfront Distribution](https://aws.amazon.com/premiumsupport/knowledge-center/api-gateway-cloudfront-distribution/)
- [AWS Documentation: Using a CNAME with Distribution](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/CNAMEs.html)


## Architecture

<p align="center">
  <img src="/architecture-diagram.drawio.svg" />
</p>


## Usage 

### Set Up

1. Add the following ssm parameters to systems manager:

- `/dns/domain/name` *value is domain name registered with aws*
- `/dns/DOMAIN_NAME/hostedZoneId` *value is hosted zone id for registered domain*

### Credentials:
```bash
export AWS_PROFILE=<profile_name>
```

### Install Dependencies:

```bash
yarn run install
```

### Deploy:

```bash
yarn run deploy
```

### Invoke Locally:

```bash
yarn run invoke <function-name>
```

### Remove:

```bash
yarn run remove
```
