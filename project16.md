## AUTOMATE INFRASTRUCTURE WITH IAC USING TERRAFORM PART 1
-
**Introduction**
-
In previous project, we had to build AWS infrastructure for 2 websites manually. We successfully deployed these components to the web but by now you'd know that DevOps is all about constant improvement, ease, convenience, comfortability and most importantly efficiency. We deployed two websites using AWS manually and you'd agree with me that the process was tedious though interesting. This is to say that things can be done differently, easily and professionally. This brings us to the first part of this project. We'd be automating infrastructure with IAC (Infrastructure and Code) using Terraform. Be rest assured, these are simple snippets codes used to create VPC and subnets on AWS. 

**WHAT IS TERRAFORM**
-
Summarily, Terraform is an open-source, infrastructure as code, software tool created by HashiCorp. Users define and provide data center infrastructure using a declarative configuration language known as HashiCorp Configuration Language, or optionally JSON. You can read more of it [here](https://en.wikipedia.org/wiki/Terraform_(software))
- For a successful implementation of this project, ensure have completed the tasks below:
- You must have completed [Terraform course](https://propitixhomes.udemy.com/course/terraform-certified/) from the Learning dashboard
- Create an IAM user, name it terraform (ensure that the user has only programatic access to your AWS account) and grant this user AdministratorAccess permissions.
- Copy the secret access key and access key ID. Save them in a notepad temporarily.
- Configure programmatic access from your workstation to connect to AWS using the access keys copied above and a [Python SDK (boto3)](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html). You must have [Python 3.6](https://www.python.org/downloads/) or higher on your workstation.
*If you are on Windows, use gitbash, if you are on a Mac, you can simply open a terminal. Read [here](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html) to configure the Python SDK properly.*

For easier authentication configuration – use [AWS CLI](https://aws.amazon.com/cli/) with aws configure command.

- Create an [S3 bucket](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html) to store Terraform state file. You can name it something like <yourname>-dev-terraform-bucket (Note: S3 bucket names must be unique unique within a region partition, you can read about S3 bucken naming in this [article](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html)). We will use this bucket from Project-17 onwards.
- To know how to install terraform and all its dependencies on windows, MacOs or Linux, ensure you watch this video [here](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli) 
- The images below should form part of your output during implementation
![aws configured](./images/aws%20configured.PNG)

![s3 bucket created](./images/s3%20bucket.PNG)

We shall now proceed to proper implementation. Please note that the above outputs represented in the images below are important in other to proceeed to this phase.
**VPC | Subnets | Security Groups**
-
First thing i did was to create a folder in my local workspace and named it `PBL` inisde which i created a file and named it `main.tf` (This file served as the point of contact for deployment). Since i've successfully configured and connected my AWS IAM account, and properly setup terraform, i added the snippets code provided in the documentation to the `main.tf` file and ran `terraform init` to initialize the new changes. The snippets code was an task for terraform to automatically create a new VPC  on my AWS IAM account. I ran `terraform plan` to review what it is about to be deployed in other to be sure they are accurate. I added more taks which was creation of 2 subnets. After reviewing and upon satisfaction, i ran `terraform apply` to deploy the chnages to my AWS account. This was done  almost immediately. I confirmed the success of the deployment and i saw the VPC and subnets created. Check below to see the images of the output gotten from the above implementation.

![terraform init](./images/terraform%20init.PNG)

![terraform plan](./images/VPC%20created.PNG)

![subnets created](./images/subnets%20creation.PNG)

I confirmed the new vpc and subnets on AWS.

![vpc confirmation](./images/VPC%20confirmation%20on%20aws.PNG)

![subnets confirmation](./images/subnets%20confirmation.PNG)

- Instead of deleting the resouces one after the other like i did in project 15, the process of automated by running `terraform destroy` on the terminal. I confirmed the deletion therefafter on my AWS. See the images below:

![terraform destroy](./images/terraform%20destroy.PNG)

![vpc deleted](./images/vpc%20deleted.PNG)

![subnets deleted](./images/subnets%20deleted.PNG)

**FIXING THE PROBLEMS BY CODE REFACTORING**
-

*Fixing Hard Coded Values:*
-

I introduced variables, and removed hard coding(In computer programming or text markup, to hardcode (less frequently, hard code ) is to use an explicit rather than a symbolic name for something that is likely to change at a later time. Such coding is sometimes known as hardcode (noun) and it is more difficult to change if it later becomes necessary.) In other to fix multiple resource blocks, loops & data sources, reconfigured the `main.tf` files to include `availability-zones` amongst other snippets. I created two files in the `PBL` folder and named it `variables.tf` and `terraform.tfvars` respectively. I separated the variable blocks available at the `main.tf`  file and pasted it in the `variables.tf` file, i configured the `terraform.tfvars` as well, aplied the new changes(The tasks still remains the same as above. Just a little modification). I applied the changes and confimed it pm AWS. The deploymemt was successful. See the images below:

![new files added](./images/new%20files%20added.PNG)

![final apply](./images/final%20apply.PNG)

![final apply](./images/final%20apply%201.PNG)

![final VPC](./images/final%20vpc.PNG)

![final subnets](./images/final%20subnets.PNG)
 This brings us to the completion of Project 16 Implementation. Thank you.