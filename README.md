# Usage
### Add below code to your provider.tf file
```
provider "helm" {
  kubernetes = {
    config_path = "~/.kube/config"
  }

  registries = [
    {
      url      = "oci://localhost:5000"
      username = "username"
      password = "password"
    },
    {
      url      = "oci://private.registry"
      username = "username"
      password = "password"
    }
  ]
}
```

### Add below code to your main.tf file
```
module name {
  source     = "SaphiaEliza/appdeploy/helm"
  name       = "nginx-ingress-controller"
  namespace  = "default"
  repository = "https://charts.bitnami.com/bitnami"
  chart      = "ingress-nginx-controller"
  wait       = false 
}
```

#### Run below command
``` 
terraform init
terraform apply
```