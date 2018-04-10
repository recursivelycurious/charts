# Helm Chart for the F5 BIG-IP Controller

This chart simplifies repeatable, versioned deployment of the [F5 BIG-IP Controller for Kubernetes](http://clouddocs.f5.com/products/connectors/k8s-bigip-ctlr/latest/).

## Requirements

The chart presumes:
- You have added a BIG-IP device to either your [Kubernetes](http://clouddocs.f5.com/containers/latest/kubernetes/kctlr-use-bigip-k8s.html) or [OpenShift](http://clouddocs.f5.com/containers/v2/openshift/kctlr-use-bigip-openshift.html) cluster.
- A partition (other than common) exists on your BIG-IP for the instance of the controller to manage.
- A secret exists in your cluster to access the BIG-IP.

The default values for the partition and the secret to access the BIG-IP are:
- `f5-bigip-ctlr` and 
- `f5-bigip-ctlr-login` 

These values can be easily updated using either `--set <param>=<value>` or `-f <values-file.yaml>`. See [customizing the chart before installing](https://docs.helm.sh/using_helm/#customizing-the-chart-before-installing) for more details.

## Chart Details

The chart creates a Deployment for one Pod containing the [k8s-bigip-ctlr](http://clouddocs.f5.com/products/connectors/k8s-bigip-ctlr/latest/) and the supporting RBAC resources.

## Installing the Chart

If using the names in the default values;

```
helm repo add f5-incubator https://f5networks.github.io/charts/incubator
helm install --set args.bigip_url=1.2.3.4 f5-incubator/f5-bigip-ctlr
```

Or

```
# from fork
helm install --set args.bigip_url=1.2.3.4 charts/src/incubator/f5-bigip-ctlr
```

## Chart parameters:

Parameter | Description | Default
----------|-------------|--------
bigip-login-secret | Secret that contains BIG-IP login credentials | f5-bigip-ctlr-login
serviceaccount | name of ServiceAccount the ctlr should use | f5-bigip-ctlr-serviceaccount
args.bigip-url | The admin IP for your BIG-IP | **Required**, no default
args.partition | BIG-IP partition the ctlr is to manage | f5-bigip-ctlr
args.log-level | Log detail | DEBUG for incubation chart
args.verify-interval | Interval in seconds to verify BIG-IP | 2 for incubation
args.node-poll-interval | Interval in seconds to poll the cluster | 1 for incubation

See the Controller documentation for a full list of [configuration parameters](http://clouddocs.f5.com/products/connectors/k8s-bigip-ctlr/v1.4/#controller-configuration-parameters).

If you have a specific use case for F5 products in the kubernetes environment that would benefit from a curated chart, please [open an issue](https://github.com/F5Networks/charts/issues) describing your use case and providing example resources.

