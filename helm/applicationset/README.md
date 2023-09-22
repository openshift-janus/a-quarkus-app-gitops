# Install
## By helm cli
example:
```
  helm install a-quarkus-app-applicationset . \
    --set applicationset.namespace=janus-argocd \
    --set helm_params.argocd.namespace="janus-argocd" \
    --set helm_params.build.cluster_subdomain="cluster-tpklj.tpklj.sandbox2638.opentlc.com" \
    --set helm_params.dev.destination.server="https://kubernetes.default.svc" \
    --set helm_params.test.destination.server="https://kubernetes.default.svc" \
    --set helm_params.prod.destination.server="https://kubernetes.default.svc" \
    --set helm_params.dev.destination.namespace="a-quarkus-app-dev" \
    --set helm_params.test.destination.namespace="a-quarkus-app-test" \
    --set helm_params.prod.destination.namespace="a-quarkus-app-prod" 
```
