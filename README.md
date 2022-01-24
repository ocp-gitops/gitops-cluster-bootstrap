# gitops-cluster-bootstrap

This repository contains the manifests to setup Red Hat OpenShift GitOps on an Red Hat OpenShift cluster. 

The bootstrap script will perform the following tasks: 
* Create a new group called `cluster-admins`, which is used in the setup for mapping permissions in ArgoCD. 
* Apply the `cluster-admin` ClusterRole to the `cluster-admins` group. 
* Install the OpenShift GitOps Operator by creating a new Subscription, making the operator available on all namespaces.
* Apply an updated `ArgoCD` custom resource to override the default instance located in the `openshift-gitops` namespace.
    * The updated `ArgoCD` custom resource applies the correct group mappings for the `cluster-admins` group. 
    * Replaces the generated certificates with an insecure server utilizing the default ingress certificate instead. 

## Assumptions

* Red Hat OpenShift 4.9.x or greater
    * Default ingress certificate replaced: https://docs.openshift.com/container-platform/4.9/security/certificates/replacing-default-ingress-certificate.html
* Red Hat OpenShift cli is installed and available in the path. 
    * https://docs.openshift.com/container-platform/4.9/cli_reference/openshift_cli/getting-started-cli.html
* bootstrap.sh assume a bash/zsh shell 

## Instructions

1. Clone this repo: `git clone https://github.com/ocp-gitops/gitops-cluster-bootstrap.git`
2. Login to Red Hat OpenShift cluster as a `cluster-admin`
3. Run `./bootstrap.sh`
4. Add appropriate users to the `cluster-admins` group. 
    * `oc adm groups add-users cluster-admins user1 user2`
