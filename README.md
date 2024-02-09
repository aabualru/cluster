## Getting started

You will first need to update the ```repoURL``` fields in the /cluster/*-app.yaml files and point it to the appropriate Git repo.

You may run the following to allow GitOps to be able to deploy in the appropriate namespaces.

``` $ oc adm policy add-role-to-user cluster-admin system:serviceaccount:openshift-gitops:openshift-gitops-argocd-application-controller```

Afterwards, you should be able to deploy this using Gitops.

## Note on Usage

This is the cluster repository.  It will allow deploying KubeCost and DynaTrace within a Kustomize strategy. Although you do need to clone the applications found in the apps repository (https://github.com/aabualru/apps), and they need to go in their own repository: in GitOps, you will simply point GitOps to this repository, at the cluster directory, and it will deploy the applications in the /apps repository on its own. In this way, it is more efficient, as it does not require anything more than adding an application manifest into the cluster directory, and that will deploy them.

## Other Instructions

After adding the application in GitOps and pointing it to the /cluster directory, be sure to press ```Refresh``` in the GitOps Console, and then press ```Sync``` to deploy them.

If you need to add more applications, simply follow the same structure of the *-app.yaml files in the cluster directory, and then add the name of the new file into the kustomization.yaml file. Then, press refresh again, and press sync again.
