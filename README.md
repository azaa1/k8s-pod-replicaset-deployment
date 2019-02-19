# k8s-pod-replicaset-deployment
Kubernetes Pod, Replica Set and Deployment

**Kubernetes Pod**: a pod is the smallest unit in Kubernetes. A pod is a capsule that contains an application container or multiple containers, storage resources and a unique network IP.

*pod.yml* file: Creates a pod called 'apache-pod'. It also attaches a label to it 'apache-app'. 
-it containes a single container called 'apache-container'.
-it pulls the image 'azaa1/httpd' from Docker Hub.
-and exposes port 80 on the container. 

*
