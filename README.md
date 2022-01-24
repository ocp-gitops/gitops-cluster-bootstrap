# gitops-cluster-bootstrap

This repository contains the manifests to setup Red Hat OpenShift GitOps on an Red Hat OpenShift cluster. 

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
