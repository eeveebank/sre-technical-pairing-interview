# NatWest Boxed SRE Technical Test

This repo will setup a local kubernetes environment that will be used during the interview. Please setup the below ahead of the interview. If you have any problems with the setup, reach out to your recruiter/the hiring manager.

## Prerequisites:

The following tools need to be installed for the test.

- [docker](https://docs.docker.com/get-docker/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [minikube](https://minikube.sigs.k8s.io/docs/start)
- [helm](https://helm.sh/docs/intro/install/)
- [skaffold at 2.13.2](https://github.com/GoogleContainerTools/skaffold/releases/tag/v2.13.2) - there's also the normal [installation instructions](https://skaffold.dev/docs/install/) but there's a [bug](https://github.com/GoogleContainerTools/skaffold/issues/9687) in v2.14.0 that breaks the setup.
- [istioctl](https://istio.io/latest/docs/ops/diagnostic-tools/istioctl/#install-hahahugoshortcode969s2hbhb)
- [Java/JDK21](https://sdkman.io/jdks#amzn)

## Getting Started

- Create a minikube cluster - `minikube start --cpus=2 --memory=4000`
- Set the kubectl context - `minikube update-context`
- Run skaffold to deploy services - `skaffold run`
- Check you have services running such as Istio, Grafana, Jaeger, Kiali and some MySQL databases - `watch kubectl get po -A`
- Check you can reach the observability addons using Istioctl - `istioctl dash kiali` OR `istioctl dash grafana` OR `istioctl dash prometheus` OR `istioctl dash jaeger`
- Tunnel to the Istio ingress - `minikube tunnel`
- Check you get a `HTTP/1.1 404 Not Found` from `istio-envoy` - `curl localhost:80 -vvv`

## Troubleshooting

To save time during the interview, please complete the above steps ahead of time. If you have any issues, you can get in touch via your recruiter/hiring manager, or troubleshoot yourself.

For example, if you are having issues with minikube tunnel, you can troubleshoot using the minikube [docs](https://minikube.sigs.k8s.io/docs/handbook/troubleshooting/).
