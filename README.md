# Edge Optimized Custom Domain Http Api Gateway w/ Cloudfront Distribution

## Info 

This handles deployment for an edge optimized custom domain http api gateway with an integrated 
lambda and distributed with a cloudfront proxy. 

HTTP APIs are designed for low-latency and cost-effective integrations, some benefits:

- support catch-all routing (which is not possible with REST APIs)
- built in JWT authorization
- global rules for CORS headers
- automatic deployments 
- trigger AWS Lambda or to another URL endpoint

With that said, HTTP APIs are still in beta and have several limitations:

- no integration with other AWS services
- Fewer configuration options
- No support for Usage plans and API Keys as with REST APIs.
- No wildcard subdomains
- Request and response transformation non existent
- No caching, validation etc. (have to be implemented in lambda logic)
- Cannot deploy edge-optimized or private API's. All deployments are regional and public
- Simple access logs and receive CloudWatch metrics, no AWS X-Ray support or ability to propagate 
logs to Kinesis Data Firehose

For Edge Optimized Api Endpoints, the default hostname of an API Gateway that is deployed 
to the specified Region while using a CloudFront distribution to facilitate client access 
typically from across AWS Regions. API requests are routed to the nearest CloudFront 
Point of Presence (POP), which typically improves connection time for geographically diverse clients.

For more information...
- [Serverless Framework: Http Support](https://www.serverless.com/blog/aws-http-api-support)
- [Serverless Framework: Http Lambda Events](https://www.serverless.com/framework/docs/providers/aws/events/http-api)
- [AWS Documentation: Http vs Rest](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-vs-rest.html)
- [AWS Documentation: Edge Optimized Apis](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-basic-concept.html#apigateway-definition-edge-optimized-api-endpoint)
- [AWS Documentation: Using a CNAME with Distribution](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/CNAMEs.html)


## Architecture

<p align="center">
  <img src="/architecture-diagram.drawio.svg" />
</p>


## Usage 

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
