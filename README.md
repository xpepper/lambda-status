# Installation
## 1. Install packages
```
npm install
```

## 2. Create lambda
```
npm run create-lambda
```

If you want to use a specific AWS profile, just adds the profile at the end of each command, like this:

```
npm run create-lambda -- --profile MY_PROFILE_NAME
```

## 3. Configure `event.json` according to your configuration.

## 4. Create an interval to execute the status check.
```
npm run add-scheduled-event
```

## 5. Create "DynamoDB table" called "status" with `id` index type `Number`

```
aws dynamodb create-table --region eu-central-1 --table-name status \
  --attribute-definitions AttributeName=id,AttributeType=N \
  --key-schema AttributeName=id,KeyType=HASH \
  --provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1 \
  --query TableDescription.TableArn --output text
```

## 6. Configure `server/` -> See [christian-fei/lambda-status-server](https://github.com/christian-fei/lambda-status-server)

# Uninstall
```
npm run destroy-lambda
```
(optionally with `-- --profile MY_PROFILE_NAME` at the end)
