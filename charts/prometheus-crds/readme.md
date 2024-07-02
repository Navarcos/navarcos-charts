# Prometheus Stack CRDs

CRDs for Prometheus Stack.
Thay can be installed in an empty cluster so that

- ServiceMonitors
- PodMonitors
- PrometheusRules

can be created by other charts without raising errors if Prometheus Stack is not yet installed.

## Install

### Helm

```shell
helm upgrade  --wprometheus-crds-navarcosait --install navarcos/prometheus-crds-navarcos
```

## Chart Update

Prometheus stack CRDs are copied from the original chart (prometheus-stack-navarcos).
