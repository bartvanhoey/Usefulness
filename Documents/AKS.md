## Azure Kubernetes Service

```bash
// Bash
export RESOURCE_GROUP=rg-contoso-video
export CLUSTER_NAME=aks-contoso-video
```

```bash
// Azure CLI
az aks create \
    --resource-group $RESOURCE_GROUP \
    --name $CLUSTER_NAME \
    --node-count 2 \
    --enable-addons http_application_routing \
    --generate-ssh-keys \
    --node-vm-size Standard_B2s \
    --network-plugin azure
```

```bash
// Azure CLI
az aks nodepool add \
    --resource-group $RESOURCE_GROUP \
    --cluster-name $CLUSTER_NAME \
    --name userpool \
    --node-count 2 \
    --node-vm-size Standard_B2s
```

### Link your Kubernetes cluster with kubectl by running the following command

```bash
// Azure CLI
az aks get-credentials --name $CLUSTER_NAME --resource-group $RESOURCE_GROUP

// Bash
kubectl get nodes

```

### Run the az network dns zone list command to query the Azure DNS zone list

```bash
// Azure CLI
az aks show -g $RESOURCE_GROUP -n $CLUSTER_NAME -o tsv --query addonProfiles.httpApplicationRouting.config.HTTPApplicationRoutingZoneName

returns:
<uuid>.<region>.aksapp.io
```

