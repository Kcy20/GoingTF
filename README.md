# GoingTF
<img src="https://image.ibb.co/bEF0B7/doggy.gif" alt="doggy" border="0">

## Fresh Terraform IaC project
- https://developer.hashicorp.com/terraform/tutorials

## Quick CMDS
```TypeScript
terraform init
terraform fmt
terraform validate
terraform plan -out=terraform.plan
terraform apply
terraform show
terraform state list
terraform destory
```


## AWS - Terraform
- Need: Terraform CLI, AWS CLI, AWS creds, store tf state files
- (terraform block) https://developer.hashicorp.com/terraform/tutorials/aws-get-started/aws-build
- (Terraform REGISTRY) https://registry.terraform.io/
- (Good read on Terraform state store) https://spacelift.io/blog/terraform-state
- (Terraform cloud for remote state) https://www.hashicorp.com/blog/using-terraform-cloud-remote-state-management

```TypeScript
 /* stored aws creds for non-root user which has AWS cli 
  */
 source (~/.aws/credentials)
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