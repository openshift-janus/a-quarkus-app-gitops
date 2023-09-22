# Install
## By helm cli
example:
```
  helm install a-quarkus-app-applications . \
    --set applicationset.namespace=janus-argocd \
    --set dev.destination="https://kubernetes.default.svc" \
    --set test.destination="https://kubernetes.default.svc" \
    --set prod.destination="https://kubernetes.default.svc" \
    --set dev.namespace=a-quarkus-app-dev \
    --set test.namespace=a-quarkus-app-test \
    --set prod.namespace=a-quarkus-app-prod 
```
