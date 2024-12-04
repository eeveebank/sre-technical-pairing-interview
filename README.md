# NatWest Boxed SRE Technical Test

## Prerequisites:

The following tools need to be installed for the test.

- [docker](https://docs.docker.com/get-docker/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [minikube](https://minikube.sigs.k8s.io/docs/start)
- [skaffold](https://skaffold.dev/docs/install/)
- [istioctl](https://istio.io/latest/docs/ops/diagnostic-tools/istioctl/#install-hahahugoshortcode969s2hbhb)

## Getting Started

- Create a minikube cluster - `minikube start`
- Set the kubectl context - `minikube update-context`
- Run skaffold to deploy services - `skaffold run`
- Check you have services running such as Istio, Grafana, Jaeger, Kiali and some MySQL databases - `watch kubectl get po -A`
- Check you can reach the observability addons using Istioctl - `istioctl dash kiali` OR `istioctl dash grafana` OR `istioctl dash prometheus` OR `istioctl dash jaeger`
- Tunnel to the Istio ingress - `minikube tunnel`
- Check you get a `HTTP/1.1 404 Not Found` from `istio-envoy` - `curl localhost:80 -vvv`
