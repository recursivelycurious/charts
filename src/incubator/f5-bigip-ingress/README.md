# Helm Chart for using the F5 BIG-IP as an ingress

This chart simplifies repeatable, versioned use of the F5 BIG-IP as an [ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) within Kubernetes or OpenShift by using the [k8s-bigip-ctlr](http://clouddocs.f5.com/containers/latest/kubernetes/kctlr-ingress.html) as an ingress controller.

## Requirements

The chart presumes:
- You have [Helm with Tiller](https://docs.helm.sh/using_helm/#installing-helm) installed on your cluster with appropriate permissions.
- You have the k8s-bigip-ctlr already running in your cluster. You can use a separate chart - the [f5-bigip-ctlr chart](https://github.com/F5Networks/charts/tree/master/src/stable/f5-bigip-ctlr) - to deploy the controller, or you can deploy it [manually](http://clouddocs.f5.com/containers/latest/kubernetes/kctlr-app-install.html). 
- The services accepting traffic from the ingress are configured separately.

> Note - This chart and the [f5-bigip-controller](https://github.com/recursivelycurious/charts/tree/wip/src/incubator/f5-bigip-ctlr) chart can be used independently or together. If you or your organization author your own charts either or both may be used as a subchart.
>
> Similarly, this ingress chart can be combined -- either as a parent chart or a subchart -- with charts that define the services accepting traffic.

## Chart Details

The chart creates an Ingress resource for use with the [k8s-bigip-ctlr](http://clouddocs.f5.com/containers/latest/kubernetes/index.html).

## Installing the Chart

Copy the `values.yaml` file and use it as the basis for your own ingress specification and then pass your custom values file when invoking `helm install`:

```
helm repo add f5-incubator https://f5networks.github.io/charts/incubator
helm install -f path/to/custom-values.yaml f5-incubator/f5-bigip-ingress
```

Or

```
# from fork
helm install -f path/to/custom-values.yaml charts/src/incubator/f5-bigip-ingress/
```

## Primary Chart parameters:

Parameter | Description | Default
----------|-------------|--------
ingress.annotations.virtual-server.f5.com/ip | IP accepting traffic on the BIG-IP | **Required** no default
ingress.annotations.virtual-server.f5.com/partition | BIG-IP partition of the Controller | **Required** no default
ingress.namespace | Kubernetes/OpenShift namespace for the ingress | Optional
spec | Backend(s) and associated hosts and paths | See [examples](https://github.com/F5Networks/charts/tree/master/example_values/f5-bigip-ingress) 

### Additional Optional parameters as annotations

The annotations listed under the `ingress.annotations` parameter are consumed as an array and any of the [documentend annotations for the k8s-bigip-ctlr](http://clouddocs.f5.com/products/connectors/k8s-bigip-ctlr/latest/#supported-ingress-annotations) may be used.

> CAUTION: Be sure to use a controller version compatable with the annotations you choose.

If you have a specific use case for F5 products in the kubernetes environment that would benefit from a curated chart, please [open an issue](https://github.com/F5Networks/charts/issues) describing your use case and providing example resources.

