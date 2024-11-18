

###### Auth #####


csv file of username and password 

that we can add in kube-apiservice as follows   
    --basic-auth-file=user-details.csv

that we can add in kube-apiservice as follows   
    --token-auth-file=user-token-details.csv



kubectl config view 



################### CUstome KubeConfig ##################

            apiVersion: v1
            kind: Config

            clusters:
            - name: production
            cluster:
                certificate-authority: /etc/kubernetes/pki/ca.crt
                server: https://controlplane:6443

            - name: development
            cluster:
                certificate-authority: /etc/kubernetes/pki/ca.crt
                server: https://controlplane:6443

            - name: kubernetes-on-aws
            cluster:
                certificate-authority: /etc/kubernetes/pki/ca.crt
                server: https://controlplane:6443

            - name: test-cluster-1
            cluster:
                certificate-authority: /etc/kubernetes/pki/ca.crt
                server: https://controlplane:6443

            contexts:
            - name: test-user@development
            context:
                cluster: development
                user: test-user

            - name: aws-user@kubernetes-on-aws
            context:
                cluster: kubernetes-on-aws
                user: aws-user

            - name: test-user@production
            context:
                cluster: production
                user: test-user

            - name: research
            context:
                cluster: test-cluster-1
                user: dev-user

            users:
            - name: test-user
            user:
                client-certificate: /etc/kubernetes/pki/users/test-user/test-user.crt
                client-key: /etc/kubernetes/pki/users/test-user/test-user.key
            - name: dev-user
            user:
                client-certificate: /etc/kubernetes/pki/users/dev-user/developer-user.crt
                client-key: /etc/kubernetes/pki/users/dev-user/dev-user.key
            - name: aws-user
            user:
                client-certificate: /etc/kubernetes/pki/users/aws-user/aws-user.crt
                client-key: /etc/kubernetes/pki/users/aws-user/aws-user.key

            current-context: test-user@development
            preferences: {}

##############################################


kubectl config --kubeconfig=/root/my-kube-config current-context

kubectl config --kubeconfig=/root/my-kube-config use-context research


override kubeconfig file 

cp my-kube-config  ~/.kube/config

k config view




###############################################################

### Role and RoleBinding 

k get roles 

k get rolebinding

k describe role 

k auth can-i create deployments

k auth can-i delete nodes


k auth can-i create deployments --as dev-user

k auth can-i delete nodes --as dev-user


