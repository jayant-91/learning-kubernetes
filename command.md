### (kind) local kubernetes cluster

$ kind create cluster --name local   // for creating a single node cluster

$ kind create cluster --config cluster.yml --name local   // for creating setup node cluster 

$ kind get clusters  // for getting all clusters

$ kind delete cluster --name local  // for delete a cluster name local


## (kubectl) command line tool for interacting with cluster 

### pod 

$ kubectl get nodes   // for getting all nodes in cluster

$ kubectl get pods    // for getting all pods deployed in cluster 

$ kubectl run nginx --image=nginx --port=80    // for running a pod 

$ kubectl apply -f manifest.yml   // for running a pod from manifest file (standerd practice)
// even though apply command only create one pod we can define multiple containers inside the pod by manifest.yml file 

$ kubectl logs nginx     // for getting all nginx pods 

$ kubectl describe pod nginx   // for see details about nginx pod 

$ kubectl delete pod nginx    // for delete nginx pod 


### deployment

// deployment manages all the replecs of a pod 
// if any pod creshes or intentionaly deleted deployment will roll-back (start again)


// create a deployment with 3 nginx pod (not recomended in production)
$ kubectl create deployment nginx-deployment --image=nginx --port=80 --replicas=3

$ kubectl get deployment   // show all the deployment in a cluster 

$ kubectl delete deployment <deployment-name>   // delete the given deployment 

$ kubectl apply -f deployment/manifest.yml   // for creating a deployment by manifest.yml(recomended)


### ReplicaSet

$ kubectl get replicaset   // get all the replicaset 
or 
$ kubectl get rs       // both commands are identical


### Service

// a service expose your pod over internet  

$ kubectl get pods -owide   // shows all the pods with there ip address


