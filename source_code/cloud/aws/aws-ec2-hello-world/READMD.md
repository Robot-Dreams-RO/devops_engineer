# Steps to deploy

```bash

terraform init
terraform plan
terraform apply

terraform output -raw private_key > key.pem
chmod 400 key.pem
```
