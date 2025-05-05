# 02_s3

## 概要

S3の構築。

---

## 構築リソース

---

## 環境変数設定

```bash
SYSTEM_ENV=# your system env

```

---

## 21_s3

### CloudFormation実行

```bash
aws cloudformation create-stack --stack-name stack-email-uploader-$SYSTEM_ENV-s3 --template-body file://template/02_s3/21_s3.yml --parameters ParameterKey=SystemEnv,ParameterValue=$SYSTEM_ENV
aws cloudformation wait stack-create-complete --stack-name stack-email-uploader-$SYSTEM_ENV-s3

```
