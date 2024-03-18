# deploy-lambda

Deploy Lambda function to Adapt AWS account

## Inputs

### `aws-region`

**Optional** AWS region to deploy to (default: eu-west-1)

### `lambda-name`

**Required** Name of the lambda function to deploy

### `node-runtime`

**Required** Node runtime for the lambda function (e.g. nodejs14.x)

### `role-to-assume`

**Required** ARN of the role to assume for deployment

## Example usage

The permissions are needed to interact with GitHub's OIDC Token endpoint. This is on the root of your workflow yaml file

```yaml
permissions:
  id-token: write
  contents: write
  statuses: write
```

The following is an example of how to use this action in a workflow:

```yaml
uses: A-dapt/deploy-lambda@v1.0
with:
  lambda-name: api-lambda
  node-runtime: nodejs18.x
  role-to-assume: ${{ secrets.AWS_ROLE_TO_ASSUME_ADAPT_CORE_PLATFORM }}
```

## Special commands

To create the lambda function, use the following in a commit message:

```
create_lambda
```

To destroy the lambda function, use the following in a commit message:

```
destroy_lambda
```
