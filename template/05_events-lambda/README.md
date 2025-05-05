# 05_events-lambda

## 概要

CDNの構築。

---

## 構築リソース

---

## 環境変数設定

```bash
SYSTEM_ENV=# your system env
USER=# your credential user
PASSWORD=# your credential password
```

---

## 51_events

### CloudFormation実行

```bash
aws cloudformation create-stack --stack-name stack-email-uploader-$SYSTEM_ENV-events --template-body file://template/05_events-lambda/51_events.yml --parameters ParameterKey=SystemEnv,ParameterValue=$SYSTEM_ENV --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM
aws cloudformation wait stack-create-complete --stack-name stack-email-uploader-$SYSTEM_ENV-events

```
