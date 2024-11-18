

Kubectl config view 

kubectl config view --kubeconfig=my-custom-config

kubectl config --kubeconfig=/root/my-kube-config current-context

kubectl config use-context <context>

kubectl config --kubeconfig=/root/my-kube-config current-context use-context <context>

k get pod --as dev-user

