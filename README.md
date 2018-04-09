# F5 Networks Helm Charts

This repository contains [helm](https://helm.sh/) for use with [F5 Networks](https://f5.com/) products and services within a [Kubernetes](https://kubernetes.io/) or [OpenShift](https://www.openshift.com/) environment.

**Note** that charts may require access to `kube-system` namespace and/or cluster wide permissions to function as expected, so be sure to install/configure helm/tiller appropriately.

To add the stable repo to helm:

```
helm repo add f5-stable https://f5networks.github.io/charts/stable
```

## Stable Charts

These charts are tested and documented:
- [f5-bigip-ctlr](https://github.com/F5Networks/charts/tree/master/src/stable/f5-bigip-ctlr) - Use this chart to deploy the [k8s-bigip-ctlr](http://clouddocs.f5.com/products/connectors/k8s-bigip-ctlr/latest/) in Kubernetes or OpenShift.
- [f5-bigip-ingress](https://github.com/F5Networks/charts/tree/master/src/stable/f5-bigip-ingress) - Use this chart to deploy ingress resources in Kubernetes or OpenShift.

To access additional charts in beta:

```
helm repo add f5-incubator https://f5networks.github.io/charts/incubator
```
