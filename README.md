Stuff we had to do:

1) Add enough compute
2) On the argocd-redis Deployment, remove the template.spec.securityContext.runAsUser setting
3) On the harness-agent-agent Deployment, change the container's securityContent.allowPrivilegeEscalation to true
4) Add the harness-agent-agent service account to the privileged SCC:

> oc adm policy add-scc-to-user privileged -z harness-agent-agent

5) Redeploy the two deployments
6) Create the Harness GitOps pipelines and deploy (note that it deploys to 'default' namespace?!)
