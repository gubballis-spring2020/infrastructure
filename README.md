## Cloud-Formation

This repo helps you deploy the resources stack on AWS and create them. For this we need to configure AWS cli to run the cloudformation template from the terminal.

1) First you need to download the aws cli. More info - https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html .

2) Configure different accounts using ```aws configure``` command and set up the access and secret keys. Info - https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html .

    ```example : aws configure --profile profile_name```

3) The template in networking.yaml file helps you create a VPC, 3 subnets, route table etc. To deploy the VPC stack run the following command and replace the variables with your input.

    ``` aws cloudformation create-stack \
    --stack-name stack_name \
    --template-body file://networking.yaml \
    --region preferred_region \
    --parameters ParameterKey=VpcCIDR,ParameterValue=VPCcidr ParameterKey=PublicSubnet1CIDR,ParameterValue=Subnet1cidr ParameterKey=PublicSubnet2CIDR,ParameterValue=Subnet2cidr ParameterKey=PublicSubnet3CIDR,ParameterValue=Subnet2cidr ParameterKey=VpcName,ParameterValue=vpc-name \
    --profile profile_name ```