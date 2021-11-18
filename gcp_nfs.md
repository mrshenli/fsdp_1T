# Create GCP NFS share

Define environment variables:
```bash
export INSTANCE_NAME="shen-nfs1"
export INSTANCE_TIER="STANDARD"
export FILE_SHARE_NAME="shen_share1"
export FILE_SHARE_CAPACITY="4TB"
export CLUSTER_ZONE="us-central1-b"
```

Create Filestore NFS share:
```bash
gcloud filestore instances create ${INSTANCE_NAME} \
	--tier=${INSTANCE_TIER} \
	--file-share=name=${FILE_SHARE_NAME},capacity=${FILE_SHARE_CAPACITY} \
	--network=name=default \
	--zone=${CLUSTER_ZONE}
```

Get IP address and share name:
```bash
gcloud filestore instances describe ${INSTANCE_NAME} \
	--zone=${CLUSTER_ZONE} \
	--format="flattened(networks[0].ipAddresses[0], fileShares[0].name)"
```
