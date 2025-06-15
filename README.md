# 🚀 Strapi CMS on AWS

This is a Strapi CMS project created using `yarn create strapi` and modified for AWS Elastic Beanstalk deployment. It uses [web-server-on-aws](https://github.com/shuo-s-feng/web-server-on-aws) for automated infrastructure creation and deployment.

## 🛠️ Development

### Prerequisites

- Node.js ~22.x
- Yarn
- AWS-related configureations. [Learn more](https://github.com/shuo-s-feng/web-server-on-aws?tab=readme-ov-file#prerequisites)

### Build

Build your admin panel. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-build)

```bash
yarn build
```

### Local Development

Start your Strapi application with autoReload enabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-start)

```bash
yarn start
```

## 🚀 AWS Deployment

### Configuration

1. Clone the [web-server-on-aws](https://github.com/shuo-s-feng/web-server-on-aws) repository in the same folder with this repository
2. Create `.env.staging` or `.env.prod` file in the web-server-on-aws directory with the following content:

```bash
# AWS Configuration
AWS_ACCOUNT='<AWS_ACCOUNT_ID, e.g. 123456789012>'
AWS_REGION='<AWS_REGION, e.g. us-east-1>'

# Node.js Backend Configuration
NODEJS_BACKEND_APP_NAME='<APP_NAME, StrapiCMS>'
NODEJS_BACKEND_SOURCE_PATH='../strapi-example'
NODEJS_BACKEND_EC2_INSTANCE_TYPE='t3.medium'
NODEJS_BACKEND_LOOSE_HEALTH_CHECK='true'
```

### Deployment

From the web-server-on-aws directory, run one of the following commands:

For staging environment:

```bash
yarn deploy-nodejs-backend:staging
```

For production environment:

```bash
yarn deploy-nodejs-backend:prod
```

This will:

1. Create necessary AWS infrastructure using CDK
2. Deploy your Strapi application to AWS Elastic Beanstalk
3. Configure auto-scaling and load balancing
