

## Troubleshooting Clusters


        kubectl get nodes 

        ## to check the health of nodes to troubleshoot issue
        kubectl describe nodes node_name 

        kubectl cluster-info

        ## give all info and logs
        kubectl cluster-info dump


        kubectl get component-status


## Troubleshooting Logs 


        #$$$$$$$$$$$$  apiserver

        kubectl logs kube-apiserver-master -n kube-system

        ############### or #####

        cat var/log/kube-apiserver.log
        cat var/log/containers/kube-apiserver-master*.log



        #$$$$$$$$$$$$  scheduler

        kubectl logs kube-scheduler-master -n kube-system

        ############### or #####

        cat var/log/kube-scheduler.log
        cat var/log/containers/kube-scheduler-master*.log


        #$$$$$$$$$$$$  controller 

        kubectl logs kube-controller-manager-master -n kube-system

        ############### or #####

        cat var/log/kube-controller-manager.log
        cat var/log/containers/kube-controller-manager-master*.log


        #$$$$$$$$$$$$  controller 

        kubectl logs etcd-master -n kube-system

        ############### or #####

        cat var/log/etcd*.log
        cat var/log/containers/etcf*.log



## Troubleshooting Services 

        ############ kubeadm ################
        
            kubectl get pods -n kube-system

            systemctl start kubelet

            systemctl enable kubelet

            systemctl start docker

            systemctl enable docker 


## Troubleshooting cluster -- worker node

        kubectl get nodes 

        ## Possible reason of failure 
            Memory issye
            network unavailability
            kubelet failure 
            CPU outage
            Process Failures

        kubectl describe node <node-name>