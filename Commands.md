---- Short form of as follows ----
po for PODS
rs for ReplicaSets
svc for Services
ns for Namespaces
netpol for Network policies
pv for Persistent olumes
pvc for PersistentVolumeClaims
sa for Service accounts
----------------------------------

alias k=kubectl 

--------Root user --------
sudo su -

#to view logs 

kubectl exec webapp -- cat /log/app.log

Kubectl get pod <pod-name> -o yaml > <pod-name.yaml>

kubetctl replace --force -f <pod-name.yaml>

kubectl delete resource-type resource-name --force

----------------------------------

Imperative commands

kubectl create deploy nginx-deployment --image=nginx:latest 

kubectl create deploy nginx-deployment --image=nginx:latest --dry-run=client -o yaml

----------------------------------

Kubectl get pvc   --- PersistendVolumeClaim 

Kubectl get pv    --- PersistendVolume
 
Kubectl get svc   --- Service

kubectl get all -A

kubectl get deploy -A

kubectl get ingress -A


----- ConfigMap creation -------

kubectl create configmap ingress-nginx-controller --namespace ingress-nginx

kubectl create serviceaccount <account-name>

---------------------- Service and Ingress --------------

kubectl expose deploy ingress-controller -n ingress-space --name ingress --port=80 --target-port=80 --type NodePort

kubectl create ingress ingress-wear-watch -n app-space --rule="/wear=wear-service:8080" --rule="/watch=video-service:8080"

// ingress-Controller practice


### Network Policy ### 

Run the command: kubectl get networkpolicy or kubectl get netpol

kubectl get pod | wc -l