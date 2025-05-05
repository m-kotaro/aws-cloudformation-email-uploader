# 04_cloudfront

## 概要

S3の構築。

---

## 構築リソース

---

## 環境変数設定

```bash
SYSTEM_ENV=# your system env
USER=# your credential user
PASSWORD=# your credential password
```

## 41_cloudfront

### CloudFormation実行

```bash
aws cloudformation create-stack --stack-name stack-email-uploader-$SYSTEM_ENV-cloudfront --template-body file://template/04_cloudfront/41_cloudfront.yml --parameters ParameterKey=SystemEnv,ParameterValue=$SYSTEM_ENV ParameterKey=User,ParameterValue=$USER ParameterKey=Password,ParameterValue=$PASSWORD --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM --region us-east-1
aws cloudformation wait stack-create-complete --stack-name stack-email-uploader-$SYSTEM_ENV-cloudfront

```
