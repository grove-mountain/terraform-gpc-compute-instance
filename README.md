# Provision a compute instance in GCP
This Terraform configuration provisions a compute instance in Google Cloud Platform.

This is largely used for demonstrating Terraform Enterprise workspaces

## Details
By default, this configuration provisions a compute instance from image debian-cloud/debian-8 with machine type t2.micro in the us-east1-b zone of the us-east1 region. But the image, type, zone, and region can all be set with variables.

### Credentials
 
You will need your GCP credentials to run Terraform in GCP.  If you don't have them already, create them:

* https://console.cloud.google.com/iam-admin/serviceaccounts
* Select the project you want to use
* Create Service Account
  * Give it a descriptive name: e.g. jlundberg-compute-admin
  * Use Compute Engine-->Compute Admin as the role
  * Check Furnish a New Private Key-->JSON
  * Save
* Download the credentials to your computer
* Change permissions to least access
  * chmod 0600 <file>
* Move file to a descriptive name: e.g. ~/.tfe_gcp_svc_account

Due to my failure to actually get the automation piece of uploading JSON in a JSON blob, you have to create the gcp_credentials file yourself in TFE.

For each gcp (and app42) workspace:
* Navigate to \<workspace>-->Variables
* Add gcp_credentials as HCL & Sensitive.   Copy text from your GCP Service Account file
* Save
