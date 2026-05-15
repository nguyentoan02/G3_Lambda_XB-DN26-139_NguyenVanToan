# NOTES

## Strategy

Chosen strategy: `serverless-http`.

This keeps the existing Express app unchanged and adds only a thin Lambda adapter.

## Why this strategy

- Minimal code change
- `app.js` remains Lambda-unaware
- `server.js` still works locally
- Live behavior matches local Express behavior

## Changes made

Added:

- `lambda.js`
- `trust-policy.json`
- `NOTES.md`

Updated:

- `package.json`
- `package-lock.json`
- `template.yaml`
- `README.md`

## Deployment

Deployment method: `aws cli` with zip package.

AWS resources created in `us-east-1`:

- Lambda function: `byol-node-express`
- IAM role: `byol-node-express-role`
- HTTP API Gateway: `byol-node-express-http-api`

## API Gateway URL

https://bkors24ac1.execute-api.us-east-1.amazonaws.com

## Verification

Verified successfully:

- `GET /`
- `GET /api/hello/Lan`
- `POST /api/echo`

## Cold start

Measured from CloudWatch Logs on 2026-05-15:

- `Init Duration: 342.09 ms`

Observed report summary:

`Duration: 30.81 ms | Init Duration: 342.09 ms | Memory Size: 512 MB`

## Note

The starter scaffold referenced `us-west-2`, but this deployment was executed in `us-east-1` based on the provided AWS environment.
