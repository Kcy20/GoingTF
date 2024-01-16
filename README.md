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

```TypeScript

```

## Docker NGINX - Terraform config 

```TypeScript
# (/GoingTF/learn-terraform-docker-container)
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