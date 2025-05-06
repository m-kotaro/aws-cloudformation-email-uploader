# 03_ses

## 概要

受信用SESの構築。

---

## 環境変数設定

```bash
SYSTEM_ENV=  # Your system environment (e.g., dev, stg, prd, 000, 111)

```

---

## 31_ses

### CloudFormation実行

```bash
aws cloudformation create-stack --stack-name stack-email-uploader-$SYSTEM_ENV-ses --template-body file://template/03_ses/31_ses.yml --parameters ParameterKey=SystemEnv,ParameterValue=$SYSTEM_ENV --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM
aws cloudformation wait stack-create-complete --stack-name stack-email-uploader-$SYSTEM_ENV-ses
export SES_RECEPTION_RULE_SET=$(aws cloudformation describe-stacks --stack-name stack-email-uploader-$SYSTEM_ENV-ses --query "Stacks[0].Outputs" --output json | jq -r '.[] | select(.OutputKey=="SESReceiptRuleSet") | .OutputValue')
aws ses set-active-receipt-rule-set --rule-set-name $SES_RECEPTION_RULE_SET

```

