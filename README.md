# ami
Repository to build ami 

1. Using AWs CLI configure two profiles:
one for dev account and one for prod account

2. Dev Command is : aws configure --profile dev - credentails of circleci user 
3. Prod command is : aws configure --profile prod - credentials of prodProfileaws user

4. How to build an ami using packer commanf:
Go to folder ami:
file vars.json should have all parameters:
1.packer validate -var-file=vars.json ubuntu-ami.json
2.packer build -var-file=vars.json ubuntu-ami.json

5.How to build ami using circleci:
1.In cicrcleCi under this repository settings add environment variables. 
2. The environment variables are:
a. aws_access_key
b. aws_secret_key
c. aws_region
d. subnet_id
e. source_ami
3. Commit in this repository.
4.Merge branch on master.
5.In circleci an ami will be created in dev account which has node env,aws cl already installed and will be shared in prod account.
6. Launch an ec2 instance using this AMI in amazon management console.
7. In ur system SSH into that created instance using 
ssh -i .ssh/awsSSHKey ubuntu@(Public Ip4 addresss of instance lunched)
updated ami with cloudwatch


