

####################  Create config #######################

## Imperative way

        ## from literal 

        kubectl create configmap config-name data-soruce

        kubectl create configmap dev-config --from-literal=key1=value1 --from-literal=key1=value1 --from-literal=key1=value1

        ## from file 

        config-map.txt
            this is config value 

        kubectl create config dev-config --from-file=/path/to/config-map.txt


        ## filename will be key and text inside file will be value 

        kubectl create config dev-config --from-file=/path/to/directory 


## Decalarative Way 

        apiVersion: v1
        kind: ConfigMap
        metadata:
            name: app-config
        data:
            app=classification
            env=prod



######################### 

kubectl exec podname -c container -- env 


### ENV 

envFrom:
    - configMapRef:
        name: app-config


### Single ENV

env:
    - name: ENV
      valueFrom:
        configMapKeyRef:
            name: app-config
            key: env

volumes:
    - name: app-config-volume
      configMap:
        name: app-config

        






