# infrastructure





## command for configure profile
```
aws configure --profile=dev

aws configure --profile=demo

```

## command for creating vpc
```
aws ec2 create-vpc \
    --cidr-block 10.0.0.0/16 \
    --amazon-provided-ipv6-cidr-block
```

## command for creating stack
Use default ciderblock
```
aws cloudformation create-stack --profile=dev --stack-name myVpc --template-body file://csye6225-infra.yml
```

Use given ciderblock
```
aws cloudformation create-stack --profile=demo --stack-name myvpc --template-body file://csye6225-infra.yml --parameters ParameterKey=VpcCidrBlock,ParameterValue="10.0.0.0/16" ParameterKey=SubCidrBlockA,ParameterValue="10.0.0.0/24" ParameterKey=SubCidrBlockB,ParameterValue="10.0.1.0/24" ParameterKey=SubCidrBlockC,ParameterValue="10.0.2.0/24" ParameterKey=AMIid,ParameterValue="ami-0e9d6e26510db3c6f"

```

Use given AMIid
```
aws cloudformation create-stack --profile=demo --capabilities CAPABILITY_NAMED_IAM --template-body file://csye6225-infra.yml --parameters ParameterKey=AMIid,ParameterValue="ami-080e6b67b736f6d90" ParameterKey=CurrentProfile,ParameterValue="demo" --stack-name myVpc
```


## command for deleting stack
```
aws cloudformation delete-stack --profile=dev  --stack-name myVpc
```

## Command for deleting bucket
```
aws --profile=demo s3 rm s3://79562bc0-5c21-11ed-aabd-027cfbe3a35b.xinyi-wu-prod --recursive
```


## Other useful command
check ```AvailabilityZone``` for your profile
```
aws ec2 describe-availability-zones --profile=[profile_name]
```

ssl
```
aws acm import-certificate --certificate fileb://prod_miffy_space.crt --certificate-chain fileb://prod_miffy_space.ca-bundle --private-key fileb://private.key
```