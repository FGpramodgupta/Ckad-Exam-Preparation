
################ Deployment ##################


kubectl create deployment redis-deployment --image redis --replicas=10


kubcetl create -f rolling-update-deployment.yml

kubectl rollout status deployment redis-deployment 

kubectl set image deploy redis-deployment container-name=redis:6.0 --record

kubectl rollout status deployment redis-deployment 

kubectl rollout history deployment redis-deployment


#### Rollback ####

kubectl rollout undu deployment redis-deployment

kubectl rollout undu deployment redis-deployment --to-revision=2
 

### ## Sclare and descale Deployment 

## update yaml file then apply 

## another way is 

kubectl scale deployment redis-deployment --replicas=3

# Auto scale a deployment "foo", with the number of pods between 2 and 10, no target CPU utilization specified so a default autoscaling policy will be used

kubectl autoscale deployment foo --min=2 --max=10

# Auto scale a replication controller "foo", with the number of pods between 1 and 5, target CPU utilization at 80%

kubectl autoscale rc foo --max=5 --cpu-percent=80

