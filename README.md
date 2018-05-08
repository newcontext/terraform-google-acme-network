# tf_module_glcoud_network

Terraform module for building out networks on Google Cloud Services

It builds a VPC network and subnetworks

## Use

Call it as a module from another Terraform repository.

```sh
module "network" {
  source = "tf_module_gcloud_network"

  organization_name = "Your Organization Name Here"
}
```

## Testing

To build, validate and then destroy run these commands below:

```sh
bundle exec kitchen converge
bundle exec kitchen verify
bundle exec kitchen destroy
```

### Prerequisites

- Ruby 2.2 or greater
- Terraform 0.10 or greater
- gcloud command line utility (https://cloud.google.com/sdk/)
- Google Cloud Project with a service account
- Download service account credentials to: `credentials.json`
- Create an environment file: `.env`, add this content:

```sh
export TF_VAR_engineer_cidrs="[\"$(dig +short myip.opendns.com @resolver1.opendns.com)/32\"]"
export GOOGLE_APPLICATION_CREDENTIALS="credentials.json"
export GCLOUD_PROJECT="<project-id>
export GCLOUD_REGION="us-west1"
```
