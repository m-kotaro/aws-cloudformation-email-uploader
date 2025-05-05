# 03_ses

## 概要

受信用SESの構築。

---

## 構築リソース

---

## 環境変数設定

```bash
SYSTEM_ENV=# your system env

```

---

## 31_ses

### CloudFormation実行

```bash
aws cloudformation create-stack --stack-name stack-email-uploader-$SYSTEM_ENV-ses --template-body file://template/03_ses/31_ses.yml --parameters ParameterKey=SystemEnv,ParameterValue=$SYSTEM_ENV --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM
aws cloudformation wait stack-create-complete --stack-name stack-email-uploader-$SYSTEM_ENV-ses

```

