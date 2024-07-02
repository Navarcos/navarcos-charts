# Prometheus Stack

## Installazione

### Helm

```shell
helm upgrade monitoring --wait --install --namespace monitoring --create-namespace --values ./local-values.yaml ./
```

### Aggiornamento

I CRD dei ServiceMonitor e dei PodMonitor vengono precaricati in prometheus-crds, altrimenti ci sono errori nel preconfigurare tutti i Monitor e nell'installazione con ArgoCD.

Quando si aggiorna `prometheus-stack` Helm vanno ricopiati i file presenti nel .tgz `charts/kube-prometheus-stack-XX.YY.ZZ.tgz` in `prometheus-crds/templates/`.

**ATTENZIONE:** Quando si aggiorna `prometheus-stack` va aggiornata anche la versione di `prometheus-crds`, **anche se non sono cambiati i CRD**

## Grafana admin username e password

Il nome utente e la password per Grafana sono autogenerati e salvati nel secret:
`<namespace>/grafana-admin`

Nel caso in cui vogliate usare i vostri modificate le variabili:

```yaml
adminUsername
adminPassword
```

che comunque vengono salvati nel secret di cui sopra.

## PodMonitor per linkerd

I PodMonitor in ./templates/prometheus-stack_linkerd_podmonitor.yaml sono presi da <https://github.com/linkerd/website/issues/853>

## AKS

### Patch per Calico per esportare le metriche

#### Patch calico to export metrics

```shell
kubectl patch felixconfiguration default --type merge -p '{"spec":{"prometheusMetricsEnabled": true}}'
```

#### Patch typha to export metrics

```shell
kubectl patch installation default --type merge -p '{"spec": {"typhaMetricsPort":9093}}'
```
