# rhsc23-pipeline

This is the repo containing the pipeline definition for the 2023 summit connect demo, updating the scoring service

Currently I have no idea what I'm doing

The pipelines and definitions are applied to the cluster via argoCD, 
In order to deploy the pipeline you must define a custom parameter of your dockercfgjson,

Current working pipeline is the new file pipeline-basic.yaml

# Enable Image Signing
To enable image signing patch the cluster with the follwoing commands 

`
oc patch configmap chains-config -n openshift-pipelines -p='{"data":{"artifacts.taskrun.format": "in-toto"}}'

oc patch configmap chains-config -n openshift-pipelines -p='{"data":{"artifacts.taskrun.storage": "oci"}}'

oc patch configmap chains-config -n openshift-pipelines -p='{"data":{"transparency.enabled": "true"}}'
`