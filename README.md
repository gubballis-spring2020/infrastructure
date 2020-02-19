## Cloud-Formation

This repo helps you deploy the resources stack on AWS and create them. For this we need to configure AWS cli to run the cloudformation template from the terminal.

1) First you need to download the aws cli. More info - https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html .

2) Configure different accounts using ```aws configure``` command and set up the access and secret keys. Info - https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html .

    ```example : aws configure --profile profile_name```

3) The template in networking.yaml file helps you create a VPC, 3 subnets, route table etc. To deploy the VPC stack run the following command and replace the variables with your input.

We can create the stack using infra.sh script by passing the parameters as mentioned below

```
sh infra.sh stack_name region aws-profile
```

And can also be run using the below command on the command line

    ``` 
    aws cloudformation create-stack \
    --stack-name stack_name \
    --template-body file://networking.yaml \
    --region preferred_region \
    --parameters ParameterKey=VpcCIDR,ParameterValue=VPCcidrValue ParameterKey=PublicSubnet1CIDR,ParameterValue=Subnet1cidrValue ParameterKey=PublicSubnet2CIDR,ParameterValue=Subnet2cidrValue ParameterKey=PublicSubnet3CIDR,ParameterValue=Subnet2cidrValue ParameterKey=VpcName,ParameterValue=vpc-name \
    --profile profile_name 
    ```

    