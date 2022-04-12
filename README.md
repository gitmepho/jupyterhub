To run jupyterhub locally, you will need to have Docker, helm, k8s, and Kind cluster running locally.

```
helm upgrade --cleanup-on-fail --install jupyterhub jupyterhub/jupyterhub --namespace jupyter --create-namespace --version=1.0.0 --values config.yaml --debug
```

If the helm deployment was successfully, you can check:

```
helm list -n jupyter #-n is the k8s namespace
```

From there you can check the k8s resources:

```
kubectl get all -n jupyter
kubectl get service -n jupyter
```

Then to get to the UI:

```
kubectl port-forward -n jupyter svc/proxy-public 8080:80
```

After that, follow steps on part 2: https://tanzu.vmware.com/developer/blog/data-science-with-python-jupyterhub-on-kubernetes-part-2/