# OKE Custom Node OS

## Objective
Enable a custom Linux Image ready for use with OKE Node Pools.

## High-level process
1.	Import a Rocky Linux image.
2.	Launch an instance from it to install the OKE node packages, OCI CLI and create OKE bootstrap script.
3.	Capture a “golden” image.
4.	Use that image to create an OKE managed node pool with the required bootstrap cloud-init.

## Step 1: 
Import the Rocky Linux image into OCI
Import the Rocky Linux image as an OCI Custom Image from Object Storage (Image Import).

## Step 2: 
Launch an instance from the imported image and run initialization (cloud-init)
Create a compute instance using the imported custom image and provide the following cloud-init script while creating the instance. This script configures the required yum repository and installs the OKE node packages.

## Step 3:
Install OCI CLI & create OKE Bootstrap Script
•	SSH into the instance and install the OCI CLI 
•	Create oke-install.sh file with below script in directory “/etc/oke”.
•	Make oke-install.sh file executable 
sudo chmod +x /etc/oke/oke-install.sh

## Step 4: 
Create a new custom image from the configured instance
After the OKE node packages, OCI CLI are installed and we have the OKE bootstrap script confgured, create a new Custom Image from this instance. This becomes your “OKE-ready” Rocky Linux image for managed node pools.

## Step 5: 
Create an OKE node pool using the latest custom image
Example: OCI CLI command to create the node pool

```bash
oci ce node-pool create --cluster-id <cluster-ocid> --compartment-id <compartment-ocid> --name "rocky-node-pool" --kubernetes-version v1.34.1 --node-shape VM.Standard.E5.Flex --node-shape-config '{"ocpus": 2, "memoryInGbs": 8}' --size 1 --placement-configs '[{"availabilityDomain": "tslF:US-ASHBURN-AD-1", "subnetId": "<node-subnet-ocid>"}]' --pod-subnet-ids '["<pod-subnet-ocid>"]' --node-image-id <custom-image-ocid> --ssh-public-key "$(cat <public-key-path>)"  --node-metadata '{"user_data":"'"<base64-encoded cloud-init script>'"}'
```
