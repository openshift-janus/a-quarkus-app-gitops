# How to install manually
1. Install the applicationset following the README in helm/applicationset/README.md
2. Install TriggerBinding in helm/build/README.md
Check the argocd status.

# Know issue
When argocd applicationset needs to recreated or deleted. Some resource will be hanging there:
* gitwebhook
* randomsecret
* pvc
You need to use `oc edit gitwebhook` and then remove the finalizer field in order to proceed.
