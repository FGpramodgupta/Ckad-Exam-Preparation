

######## Taints Node ##########

kubectl taint nodes node-name key=value:taint-effect

what happens to PODs that DO NOT TOLERATE this taint?

        NoSchedule
        PreferNoSchedule
        NoExecute

kubectl taint nodes node01 app=blue:NoSchedule

k taint nodes node01 app=blue:NoSchedule-

########### Tolerance ################

apiVersion: v1
kind: pod
metadata:
    name: myapp-pod
spec:
    containers:
        - name: nginx-container
        image: nginx
    tolerations:
    - key: "app"
      operator: "Equal"
      value: "blue"
      effect: "NoSchedule"


############# Node Selector #################


Kubectl label nodes <node-name> <label-key>=<label-value>

kubectl label nodes node-1 size=Large


apiVersion: v1
kind: pod
metadata:
    name: myapp-pod
spec:
    containers:
    - name: nginx-container
        image: nginx
    nodeSelector:
        size: Large 


#### Multiple node is not fesible in nodeSelector Node Affinity 
#### support multiple Node Affinity


apiVersion: v1
kind: pod
metadata:
    name: myapp-pod
spec:
    containers:
    - name: nginx-container
      image: nginx
    affinity:
        nodeAffinity:
            requiredDuringSchedulingIgnoredDuringExecution:
                nodeSelectorTerms:
                - matchExpressions:
                    - key: size
                      operator: In  ## NotIn ### Exists
                      values:
                      - Large
                      - Medium


