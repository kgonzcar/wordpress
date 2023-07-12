# WordPress Demo
Testing ArgoCD and this WordPress deployment for demo purposes using Portworx and OCP 4.12

## Installation

1. From OperatorHub, enable: Red Hat OpenShift GitOps
2. Give service account of ArgoCD the ability to manage the cluster by login in to OC CLI using `kubeadmin`, and to log into Argo UI we need to get the Argo password:

Command # 1 Add cluster role to user:
- oc adm policy add-cluster-role-to-user cluster-admin -z openshift-gitops-argocd-application-controller -n openshift-gitops

Command # 2 Get Argo password
- argoPass=$(oc get secret/openshift-gitops-cluster -n openshift-gitops -o jsonpath='{.data.admin\.password}' | base64 -d)
  echo $argoPass

*Credits: https://www.youtube.com/watch?v=pOGMSOotSn0