# knative-charts

*Helm Charts for Knative*

Currently served from http://riff-incubator.cfapps.io/

To add the riff-incubator repo to Helm use:
```bash
helm repo add riff-incubator http://riff-incubator.cfapps.io/
helm repo update
```

> You need Helm version v2.10.0-rc.2 or later to get the CRDs installed with the chart. Otherwise first apply the file: https://raw.githubusercontent.com/istio/istio/1.0.0/install/kubernetes/helm/istio/templates/crds.yaml

To install Knative Serving on Minikube cluster (using NodePort) use:
```bash
helm install riff-incubator/istio --name istio --namespace istio-system --values http://riff-incubator.cfapps.io/values/values-istio-knative.yaml --set ingressgateway.service.type=NodePort
helm install riff-incubator/knative-istio --name knative-istio --namespace istio-system --set knative.ingressgateway.service.type=NodePort
helm install riff-incubator/knative-build --name knative-build --namespace knative-build
helm install riff-incubator/knative-serving --name knative-serving --namespace knative-serving
```

To install Knative Serving on GKE cluster use:
```bash
helm install riff-incubator/istio --name istio --namespace istio-system --values http://riff-incubator.cfapps.io/values/values-istio-knative.yaml
helm install riff-incubator/knative-istio --name knative-istio --namespace istio-system
helm install riff-incubator/knative-build --name knative-build --namespace knative-build
helm install riff-incubator/knative-serving --name knative-serving --namespace knative-serving
```
