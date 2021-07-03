# Project _pod_ tato Head - A demo project for showcasing cloud-native application delivery use cases using different tools for various use cases

![podtatohead](/images/podtatoHead.png)

## What you are getting

This project consists of the smallest possible application to demo cloud native
application delivery. It - for sure - will grow over time. Right now you get the following components:

* A single file go server that displays different versions of the podtato-head depending on the version
* A multi-stage build docker file to build a container
* A manifest to create a Kubernetes service and deployment.
* A helm chart for the service and the deployment.
* Three container images showing different versions

  * ghcr.io/sumantan/podtatoserver:v0.1.0
  * ghcr.io/sumantan/podtatoserver:v0.1.1
  * ghcr.io/sumantan/podtatoserver:v0.1.2

## Scenarios and Use Cases you can test with this repository

This list is supposed to grow over time. Here is the list of use cases, that are
currently supported:

* [Direct deployment via a manifest](/delivery/manifest/README.md)
* [Direct deployment via a Helm chart](/delivery/charts/README.md)
* [Direct deployment via Kustomize](/delivery/kustomize/README.md)
* [Direct deployment via Ketch](/delivery/ketch/README.md)
* [Direct deployment via Kapp](/delivery/kapp/README.md)
* [GitOps-based deployment using Flux](/delivery/flux/README.md)
* [GitOps-based deployment using ArgoCd](/delivery/ArgoCD/README.md)
* [Canary releases via Argo Rollouts](/delivery/rollout/README.md)
* [Helm-based operator deployment](/delivery/podtato-operator/README.md)
* [Multi-Stage delivery with Keptn](/delivery/keptn/README.md)
* [CNAB with Porter air-gapped deployment](/delivery/CNABwithPorter/README.md)
* [GitOps-based deployment using KubeVella](/delivery/KubeVela/README.md)
* [GitOps-based deployment using Gimlet CLI](/delivery/gimlet/README.md)

Use cases supported going foward:

* multiple services in different version
* stateful workloads
* external dependencies
* _feel free to create issues for use cases you are interested in_

## Cluster environment

You can use any K8S cluster to run this project.
If you do not have a K8S cluster at your disposal, you can quickly get a local one with [kind](https://kind.sigs.k8s.io/docs/user/quick-start/).

_NOTE_: If you use a cluster with no access to external LoadBalancer (like a `kind` cluster), you may have to replace `type: LoadBalancer` by `type: ClusterIP` (or `type: NodePort`) in all `service.yaml` manifests :

```
find delivery -type f -name "*.yaml" -print0 | xargs -0 sed -i 's/type: LoadBalancer/type: ClusterIP/g'
```

## Contributing

If you are interested in contribution to podtato head please read [contributing.md](contributing.md)
