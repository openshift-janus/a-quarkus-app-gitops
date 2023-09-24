# How to install manually
1. Install the applicationset following the README in helm/applicationset/README.md
2. Install TriggerBinding in helm/build/README.md
Check the argocd status.
3. Create secret for sonarqube acccess token , it should name as: "sonarqube-access-token", key as: "token"
4. Create secret: gpg-public-key, key as: public.key
5. Create a secret: quay-creds, create two key as: username and password
  * annotate this secret as
  ```
  kind: Secret
metadata:
  annotations:
    tekton.dev/docker-0: https://quay.apps.cluster-tpklj.tpklj.sandbox2638.opentlc.com
```
  * Add this secret to your serviceaccount pipeline
  Finally, the build task would find this secret to do authentication

# Know issue
When argocd applicationset needs to recreated or deleted. Some resource will be hanging there:
* gitwebhook
* randomsecret
* pvc
You need to use `oc edit gitwebhook` and then remove the finalizer field in order to proceed.
