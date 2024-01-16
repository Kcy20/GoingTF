# GoingTF
<img src="https://image.ibb.co/bEF0B7/doggy.gif" alt="doggy" border="0">

## Learn Terraform IaC
- https://developer.hashicorp.com/terraform/tutorials

## Quick CMDS
```TypeScript
terraform init
terraform plan -out=terraform.plan
terraform apply
terraform destory
```

## AWS - Terraform
- (Terraform CLI req) https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli
- (AWS CLI req) https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
- (AWS account req) https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all
- (AWS creds req IAM) https://docs.aws.amazon.com/IAM/latest/UserGuide/security-creds.html
 - added creds to file to 
```TypeScript
 source (~/.aws/credentials)
```

```TypeScript

```

## Docker NGINX - Terraform config 
/GoingTF/learn-terraform-docker-container
```TypeScript
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0.1"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name         = "nginx"
  keep_locally = false
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.image_id
  name  = "tutorial"

  ports {
    internal = 80
    external = 8000
  }
}
```