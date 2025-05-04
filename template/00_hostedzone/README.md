# 00_hostedzone

## 概要

DNSおよびドメインの登録と証明書の構築。

---

## 構築リソース


---

## 環境変数設定

下記コマンドで環境変数を設定する。

```bash
SYSTEM_ENV=# your system env
DOMAIN_NAME=# your Domain
```

## 01_hostedzone

### CloudFormation実行

```bash
aws cloudformation create-stack --stack-name stack-email-uploader-$SYSTEM_ENV-hostedzone --template-body file://template/00_hostedzone/01_hostedzone.yml --parameters ParameterKey=SystemEnv,ParameterValue=$SYSTEM_ENV ParameterKey=DomainName,ParameterValue=$DOMAIN_NAME
```

### ドメイン登録

#### NSレコード取得

下記コマンドを実行

```bash
export OUTPUTS=$(aws cloudformation describe-stacks --stack-name stack-email-uploader-$SYSTEM_ENV-hostedzone --query "Stacks[0].Outputs" --output json)

export HOSTEDZONE_ID=$(echo "$OUTPUTS" | jq -r '.[] | select(.OutputKey=="HostedZoneId") | .OutputValue')
export HOSTEDZONE_NAME=$(echo "$OUTPUTS" | jq -r '.[] | select(.OutputKey=="HostedZoneName") | .OutputValue')
export HOSTEDZONE_NS=$(echo "$OUTPUTS" | jq -r '.[] | select(.OutputKey=="HostedZoneNs") | .OutputValue')

echo -e "## HostedZoneNs\n$(echo "$HOSTEDZONE_NS" | tr ',' '\n')\n\n## HostedZoneName\n$HOSTEDZONE_NAME"

```


---

## 02_acm

### CloudFormation実行

