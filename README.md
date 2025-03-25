# Deploy a AWS EC2 Instance using Terraform

This guide provides step-by-step instructions to create a minimal AWS EC2 instance using Terraform and push the configuration to GitHub.

## Prerequisites

Ensure you have the following installed:
- [Terraform](https://developer.hashicorp.com/terraform/downloads)
- [AWS CLI](https://aws.amazon.com/cli/) (Configured with IAM credentials)
- [Git](https://git-scm.com/downloads)
![Screenshot 2025-03-02 124214](https://github.com/user-attachments/assets/ec9b6a3b-c2fa-4a02-a9ce-7846f5ff221e)

![Screenshot 2025-03-02 124221](https://github.com/user-attachments/assets/e7d90a6f-ffa7-417a-b488-08f2d9f8310d)

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

![Screenshot 2025-03-02 124305](https://github.com/user-attachments/assets/7e5bb69d-bdd0-4d38-9fd8-94421624dad5)

## Step 3: Initialize, Plan & Apply Terraform

Run the following commands to provision the EC2 instance:

```bash
terraform init
terraform plan
terraform apply -auto-approve
```
![Screenshot 2025-03-02 124050](https://github.com/user-attachments/assets/7853164e-f755-4104-843e-aaf8ecd2071e)
![Screenshot 2025-03-02 124101](https://github.com/user-attachments/assets/b8c5f628-ec02-4bc1-a6f0-24c6fb3c3706)

## Step 4: Confirming the Deployment
Go to the AWS Console
Navigate to EC2 → Instances
Verify that your instance is running 🎉
![Screenshot 2025-03-02 124026](https://github.com/user-attachments/assets/552cc8ac-9c31-4a1e-8b29-a62a0efa858e)

## Step 5: Destroy the Instance (Optional)

To delete the instance and clean up resources:

```bash
terraform destroy -auto-approve
```
![Screenshot 2025-03-02 124520](https://github.com/user-attachments/assets/931f29e9-1483-491d-9509-5352be3cba95)

## Conclusion

This Terraform setup creates a minimal AWS EC2 instance and stores the configuration in GitHub. You can modify `main.tf` to customize your instance settings.

---

**Happy Coding! 🚀**
