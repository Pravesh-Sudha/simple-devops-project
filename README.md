# Simple DevOps Project 🚀💯🚀

This project demonstrates how to create a simple DevOps pipeline to host a static portfolio website on AWS S3. The website includes an `index.html`, an `error.html`, and a `profile.jpg` file. The S3 bucket is configured to be public so that the website can be accessed by anyone on the internet.

## Prerequisites

Before you begin, ensure you have the following prerequisites:

1. An AWS account.
2. AWS CLI installed and configured with appropriate access rights.
3. The website files (index.html, error.html, and profile.jpg) you want to host.
4. [Terraform](https://www.terraform.io/downloads.html) installed on your local machine.

## Project Structure

```bash
project-directory/
│
├── index.html
├── error.html
├── profile.jpg
├── main.tf
├── variables.tf
├── outputs.tf
└── README.md
```

## Deployment Steps

Follow these steps to deploy your static portfolio website on AWS S3 using Terraform:

1. **Clone or Initialize Your Terraform Configuration:**

   Initialize your Terraform configuration by running the following command in your project directory:

   ```bash
   terraform init
   ```

2. Edit `main.tf` (Terraform Configuration):

Customize the main.tf file with your AWS S3 bucket configuration. Here's an example:

    ```bash
    provider "aws" {
    region = "your-preferred-region"
    }

    resource "aws_s3_bucket" "portfolio_bucket" {
    bucket = "your-unique-bucket-name"
    acl    = "public-read"
    }

    resource "aws_s3_bucket_object" "index_html" {
    bucket       = aws_s3_bucket.portfolio_bucket.id
    key          = "index.html"
    source       = "index.html"
    content_type = "text/html"
    }

    # Repeat for error.html and profile.jpg
    ```

3. Deploy Your Terraform Configuration:

    Run the following Terraform commands to apply your configuration:

    ```bash
    terraform plan
    terraform apply
    ```

4. Access Your Portfolio Website:

    Your website is now live at `http://your-unique-bucket-name.s3-website-your-preferred-region.amazonaws.com`.

5. Cleanup (Optional):

    To delete the resources created by Terraform, run:

    `terrafrom destroy`


## Usage

 Clone the repo:

`git clone https://github.com/Pravesh-Sudha/simple-devops-project.git`

