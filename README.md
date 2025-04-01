# demo_kubernetes
This is my first project in Kubernetes learning. This is a single-node cluster using Minikube. 

Description:
This project is about voting for the votes and viewing the winner.
For voting and viewing the results, we need two applications
Then, to process the votes and update them in the database, we need three applications.
We need 5 applications to complete the project.
Steps:
1. Deploying 5 pods
2. Establishing connectivity between the pods for voting and processing everything.

To establish the connectivity, I have 4 services.
2 - Nodeport, 2 - clusterIp
Nodeport service is used for working with external users. Here in this example, voting the vote and viewing the result
ClusterIP service is used for establishing the connectivity between the redis and postgres to process the votes.

Note:
We are using the services because if we use connectivity directly with the pods, there may be a chance of pod creation due to load.
So, to avoid the availability and infrastructure issues, I have used services to make the connectivity.

Commands:
kubectl create -f voting-app-pod.yaml
kubectl create -f result-app-pod.yaml
kubectl create -f postgres-pod.yaml
kubectl create -f redis-pod.yaml
kubectl create -f voting-app-service.yaml
kubectl create -f result-app-service.yaml
kubectl create -f worker-app-pod.yaml

To access, get the URL
minikube service voting-app --url


I have used the Docker images of the Kodekloud platform for voting, results, and worker. Remaining Redis and PostgreSQL are inbuilt Docker Hub repositories.
