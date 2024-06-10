# Tigera Operator / Calico

## Install

### Helm
```shell
helm upgrade tigera-crds --wait --install --namespace tigera-operator --create-namespace navarcos/tigera-crds-navarcos
helm upgrade tigera-operator --wait --install --namespace tigera-operator --create-namespace navarcos/tigera-operator-navarcos
```

## Values for an Azure cluster

### For Calico

- https://raw.githubusercontent.com/kubernetes-sigs/cluster-api-provider-azure/main/templates/addons/calico.yaml

### For Tigera Operator helm chart

- https://capz.sigs.k8s.io/topics/addons.html

- https://raw.githubusercontent.com/kubernetes-sigs/cluster-api-provider-azure/main/templates/addons/calico/values.yaml

- https://raw.githubusercontent.com/kubernetes-sigs/cluster-api-provider-azure/main/templates/addons/calico/felix-override.yaml
