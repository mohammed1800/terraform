# Deploy a AWS EC2 Instance using Terraform

This guide provides step-by-step instructions to create a minimal AWS EC2 instance using Terraform and push the configuration to GitHub.

## Prerequisites

Ensure you have the following installed:
- [Terraform](https://developer.hashicorp.com/terraform/downloads)
- [AWS CLI](https://aws.amazon.com/cli/) (Configured with IAM credentials)
- [Git](https://git-scm.com/downloads)

## Step 1: Initialize a Terraform Project

```bash
mkdir terraform-aws-instance && cd terraform-aws-instance
```

## Step 2: Create Terraform Configuration File

Create a `main.tf` file and add the following content:

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "minimal" {
  ami           = "ami-0c55b159cbfafe1f0"  # Amazon Linux 2 AMI (Change based on your region)
  instance_type = "t2.micro"

  tags = {
    Name = "MinimalInstance"
  }
}
```

## Step 3: Initialize, Plan & Apply Terraform

Run the following commands to provision the EC2 instance:

```bash
terraform init
terraform plan
terraform apply -auto-approve
```

## Step 4: Confirming the Deployment
Go to the AWS Console
Navigate to EC2 → Instances
Verify that your instance is running 🎉

## Step 5: Destroy the Instance (Optional)

To delete the instance and clean up resources:

```bash
terraform destroy -auto-approve
```

## Conclusion

This Terraform setup creates a minimal AWS EC2 instance and stores the configuration in GitHub. You can modify `main.tf` to customize your instance settings.

---

**Happy Coding! 🚀**
