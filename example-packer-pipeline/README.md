All commands run from this directory: packer-test

Example:

```
packer init .
packer build -var-file=dev.pkrvars.hcl .
```
**Note**

Windows Powershell - to make it run set the vars like this:
```
$env:PKR_VAR_compartment_ocid="ocid1.compartment.oc1...."
$env:PKR_VAR_subnet_ocid="ocid1.subnet.oc1.eu-fran.."
$env:PKR_VAR_base_image_ocid="ocid1.image.oc1...."

packer build .
```