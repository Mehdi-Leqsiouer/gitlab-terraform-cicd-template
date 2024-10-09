# linter-template

## CICD Templates
This repo implements Gitlab CI/CD templates for terraform


## Usage
```yaml
include:
- project: "badgerworks/cicd-template/terraform-template"
    ref: <version_tag>
    file: "tf.yml"
```


## Configuration 
It uses the following variables, variable that does not have default needs to be set. All required

| Name                  | description                                                                     | default value        |
|-----------------------|---------------------------------------------------------------------------------|----------------------|
| `TERRAFORM_DIR`       | subdir where terraform scripts reside                                           | `terraform`          |
| `DESTROY_ENABLE`      | failsafe to prevent resource description. If set to 'true', this step is manual | `false`              |
| `GCP_PROJECT_NAME`    | GCP project name                                                                | ``                   |
| `GCP_PROJECT_ID`      | GCP project ID                                                                  | ``                   |
| `GCP_POOL_ID`         | GCP WIF pool name                                                               | `pool`        |
| `GCP_PROVIDER_ID`     | GCP WIF provider id configured                                                  | `gitlab-tech` |
| `GCP_SERVICE_ACCOUNT` | GCP Service account for CICD                                                    | ``                   |
| `TFVARS_FILE`         | Name of tvars file                                                              | `terraform.tfvars`   |
| `GCP_ENV`             | Environment                                                                     | `dev`                |


This template automatically inject variales in TF_VAR_X :

| Tf variable                 | Gitlab CI variable                                                             
| -------------------- | ------------------------------------------------------------------------------------- 
| `project_id`     | GCP_PROJECT_NAME |
| `environment`     | GCP_ENV |
| `country`     | COUNTRY |
| `region`     | GCP_REGION |
| `application_id`     | APPLICATION_ID |
| `workload`     | WORKLOAD |

It means these variable will be accessible in your terraform files
