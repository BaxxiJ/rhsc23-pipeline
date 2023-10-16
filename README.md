# rhsc23-pipeline

How to apply pipeline to a cluster:

Install Openshift Gitops operator and Openshift Pipelines operator,
Open Openshift gitOps argoCD service route,
Add edit permissions for destination namespace to gitops svc account
Ensure group for ArgoCD admins is established
Create new app in ArgoCD:
  Use the follwoing parameters: 
    project: default
    repo url: https://github.com/BaxxiJ/rhsc23-pipeline.git
    path: config/pipeline/charts/globex-ui/
    cluster URL: https://kubernetes.default.svc
  Click create:
Add parameters to group, dockercfgjson and git token for Argo to authenticate with registry and git respectively

# Directory structure:

config/pipeline/charts/globex-ui

  Values.yaml - is the app.properties for the pipeline, defines all the static parameters
  /templates - contains all the objects needed to build the pipeline, steps, pipeline definition, triggers, event listeners etc.

gitops/application/globex

  /base - all the services to deploy the globex app (not needed)
  /overlays - kustomize overlays to apply the env-specific runtime vars
