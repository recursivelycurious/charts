# F5 Networks Helm Charts

This repository contains [helm](https://docs.helm.sh/using_helm/#using) charts for use with some [F5 Networks](https://f5.com/) products and services within a [Kubernetes](https://kubernetes.io/) or [OpenShift](https://www.openshift.com/) environment.

**Note** that charts may require access to `kube-system` namespace and/or cluster wide permissions to function as expected, so be sure to install/configure helm/tiller appropriately.

## Stable Charts

To add the stable repo to helm:

```
helm repo add f5-stable https://f5networks.github.io/charts/stable
```

These charts are tested and documented:
- [f5-bigip-ctlr](https://github.com/F5Networks/charts/tree/master/src/stable/f5-bigip-ctlr) - Use this chart to deploy the [k8s-bigip-ctlr](http://clouddocs.f5.com/products/connectors/k8s-bigip-ctlr/latest/) in Kubernetes or OpenShift.
- [f5-bigip-ingress](https://github.com/F5Networks/charts/tree/master/src/stable/f5-bigip-ingress) - Use this chart to deploy ingress resources in Kubernetes or OpenShift.

## Documentation

Each chart contains its own `README.md` and the `values.yaml` file includes notes on default values and links to the core documentation for the resources each chart is deploying.

## Incubation Charts

To access additional charts in a development or testing mode that may not be documented:

```
helm repo add f5-incubator https://f5networks.github.io/charts/incubator
```

