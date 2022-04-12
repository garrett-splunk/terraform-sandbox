# terraform-sandbox

## Requirements
1. Splunk instance with access token
2. [Terraform (minimum) v0.14](https://learn.hashicorp.com/tutorials/terraform/install-cli?in=terraform/certification-associate-tutorials)

## Initialise Terraform

```
$ terraform init --upgrade
```

## Create a workspace for the prospect (Optional)

```
$ terraform workspace new <my_prospect/name>
```
Where `<my_prospect/name>` is the company name of the prospect

## Review the execution plan

```
$ terraform plan -var="access_token=<token>" -var="realm=<realm>"
```

Where `<token>` is the Splunk Access Token (found in settings --> access token) and `<realm>` is either `eu0`, `us0`, `us1` or `us2` (found in user profile)

## Apply the changes

```
$ terraform apply -var="access_token=<token>" -var="realm=<realm>"
```

## Destroy everything!

If you created a workspace you will first need to ensure you are in the correct workspace e.g.

```
$ terraform workspace select <my_prospect/name>
```
Where `<my_prospect/name>` is the company name of the prospect

```
$ terraform destroy -var="access_token=<token>" -var="realm=<realm>"
```

## Deploying a module
After adding additional modules in modules folder - examples of applying:
```
terraform apply -var="access_token=<token>" -var="realm=<realm>" -target=module.aws
terraform apply -var="access_token=<token>" -var="realm=<realm>" -target=module.dashboards
terraform apply -var="access_token=<token>" -var="realm=<realm>" -target=module.gcp
```

# Resources 
- [tjohander's brain and repo](https://github.com/tjohander-splunk/charts-as-code)
- [signalfx terraform registry](https://registry.terraform.io/providers/splunk-terraform/signalfx/latest/docs)