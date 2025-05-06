# 05_events-lambda

## 概要

受信したEmailを解析してコンテンツ配置用バケットへ添付されたファイルを格納するスクリプトの構築。

---

## 環境変数設定

```bash
SYSTEM_ENV=# your system env
```

---

## 51_events-lambda

### CloudFormation実行

```bash
aws cloudformation create-stack --stack-name stack-email-uploader-$SYSTEM_ENV-events-lambda --template-body file://template/05_events-lambda/51_events-lambda.yml --parameters ParameterKey=SystemEnv,ParameterValue=$SYSTEM_ENV --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM

```
