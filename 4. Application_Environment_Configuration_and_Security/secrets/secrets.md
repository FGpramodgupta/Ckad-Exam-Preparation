

##### Secrets ######

Sample: 

secret Name: db-access-details
UserName: sqladmin
Password: hr@123456


### Imprerative way

   -  save username and password in .txt
       
      echo -n 'sqladmin' > ./username.txt
      echo -n 'hr@12345' > ./password.txt

      kubectl create secret [Type] [Name] [Data]

      kubectl create secret generic db-access-details --from-file=./username.txt --from-file=./password.txt

Types of Secrets:

    Opaque Secrets - The default Secret type 
    Service account token Secrets - Used to store a token that identifies a service account

    Docker config Secrets - Stores the credentials for accessing a Docker Register 

    basic auth secrets 

    SSH authentication secrets 

    TLS secrets 

    Bootstrap token secrets 

### Declarative way 

    encrypt in base64 

    echo -n 'sqladmin' | base64 

    echo -n 'hr@123456' | base64 


    apiVersion: v1
    kind: Secret
    metadata:
        name: dotfile-secret
    type: Opaque
    data:
        UserName: dmFsdWUtMg0KDQo=
        password: dmFsdWUtMg0KDQo=










####################  Create config #######################

## Imperative way

        ## from literal 

        kubectl create secret secret-name data-soruce

        kubectl create secret dev-secret --from-literal=key1=value1 --from-literal=key1=value1 --from-literal=key1=value1

        ## from file 

        secret-map.txt
            this is secret value 

        kubectl create secret dev-secret --from-file=/path/to/secret-map.txt


        ## filename will be key and text inside file will be value 

        kubectl create secret dev-secret --from-file=/path/to/directory 


## Decalarative Way 

        apiVersion: v1
        kind: Secret
        metadata:
            name: app-secret
        data:
            app=classification
            env=prod



######################### 

kubectl exec podname -c container -- env 


### ENV 

envFrom:
    - secretRef:
        name: app-secret


### Single ENV

env:
    - name: ENV
      valueFrom:
        secretKeyRef:
            name: app-secret
            key: env

volumes:
    - name: app-secret-volume
      secret:
        name: app-secret

        









