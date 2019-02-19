# Kubernetes: *Pod, Replicaset, and Deployment.*

## *Kubernetes Pod, Replica Set and Deployment.*


#### Kubernetes Pod: A *pod* is the smallest unit in Kubernetes. A pod is a capsule that contains an application container or multiple containers, storage resources and a unique network IP.

*pod.yml* file: Creates a *pod* called 'apache-pod'. It also attaches a label 'app=apache-app' to it. 

-it containes a single container called 'apache-container'.

-it pulls the image 'azaa1/httpd' from Docker Hub.

-and exposes port 80 on the container. 

#### To create the *pod* run: kubectl create -f pod.yml 


#### Kubernetes ReplicaSet: A *ReplicaSet* ensures that a specified number of pod replicas are running at any given time. This resource used when you need to keep a set number of pods running. This is good solution only if you will be doing custom updates to the pods or the pods don't require updates at all.

*replicaset.yml* file: Creates a *ReplicaSet* called 'apache-rs'. It also attaches 2 labels 'app=apache-app' and 'tier=frontend' to it.

-it sets the number of replicas to 3. 

-the selector field is used to detemine which pods the *ReplicaSet* manages. 

-it attaches 2 labels 'tier=frontend' and 'app=apache-app'on the containers.

-it pulls the image 'azaa1/httpd' from Docker Hub. 

-and exposes port 80 on the container. 

#### To create the *ReplicaSet* run: kubectl create -f replica-set.yml 


#### Kubernetes Deployment: A *Deployement* is a higer-level concept than *ReplicaSet*. It manages *ReplicaSets* and *Pods*, and allow for easy updating of a *ReplicaSet* as well as ability to roll back to a previous deployment. 

![screen shot 2019-02-19 at 12 41 42 am](https://user-images.githubusercontent.com/42782612/52996396-1d14b580-33e3-11e9-8804-8e928941f9ce.png)


*deployment.yml* file: Creates a *Deployment* called 'apache-deployment'. It also attaches label 'apache-app' to it. 

-it sets the number of replicas to 3. 

-the selector field determines which pods are part of this deployment. 

-the template field is used to specify the pods that needs to be created. 

-it attaches a label 'app=apache-app' to the containers. 

-it pulls the image 'azaa1/httpd' from Docker Hub. 

-and exposes port 80 on the container. 

#### To Create the *Deployment* run: kubectl create -f deployment.yml 


#### NOW that the pods are created we need a *Kubernetes Service* to publish the pods. In this example we are creating a LoadBalancer Service. 

*service.yml* file: Creates a *Service* called 'apache-service', type is LoadBalancer. 

-the selector section selects the pods with label 'app=apache-pod'. 

-under ports, it listens to port 8080, and forwards the traffic to port 80 of the *pods*. 

-note the *pods* are running *APACHE* and as *APACHE* listens to port 80 the traffic is forward to port 80. 

-you can configure port 80 to the port of that your application listens to. 

#### To Create the *Service* LoadBalancer run: kubectl create -f service.yml 
### -NOTE this works on the Cloud Providers that support LoadBalancers. 

#### To Check if the pods are successfully published: Open your browser enter: < IP-of-LoadBalancer:8080 >

