# Install pipeline
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

# Install TriggerBinder
```
cat <<EOF | oc apply -f -
apiVersion: triggers.tekton.dev/v1alpha1
kind: TriggerBinding
metadata:
  creationTimestamp: null
  name: a-quarkus-app-binding
  namespace: "a-quarkus-app-dev"
spec:
  params:
  - name: maven_mirror_url
    value: 'http://nexus-sonatype-nexus-service.nexus.svc:8081/repository/maven-public/'
  - name: sonarqube_host_url
    value: "http://sonarqube.sonarqube.svc:9000"
  - name: image_repo
    value: "quay.apps.cluster-tpklj.tpklj.sandbox2638.opentlc.com/dev/a-quarkus-app"
  - name: image_test_repo
    value: "quay.apps.cluster-tpklj.tpklj.sandbox2638.opentlc.com/test/a-quarkus-app"
  - name: cyclonedx_host_url
    value: "https://cyclonedx-bom-repo-server-cyclonedx.apps.cluster-tpklj.tpklj.sandbox2638.opentlc.com"
EOF
```
