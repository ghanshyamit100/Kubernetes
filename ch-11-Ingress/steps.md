ngress demonstration
This is a demonstration of how to use Kubernetes Ingress to route traffic to different services in your cluster based on different paths.

Install nginx-ingress controller :
To get started, you will need to install the nginx-ingress controller in your Kubernetes cluster by running the following command:

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
This will deploy the nginx-ingress controller as a Deployment in your cluster.

Create Deployments
Next, you will need to create some sample Deployments to route traffic to. Run the following commands to create the Deployments:

kubectl apply -f deploy-sample-1.yaml
kubectl apply -f deploy-sample-2.yaml
kubectl apply -f deploy-sample-3.yaml
kubectl apply -f deploy-sample-4.yaml

These commands will create four sample Deployments with different images.

Create services
After you have created the Deployments, you will need to create Services for each of them. Run the following commands to create the Services:

kubectl expose deploy sample-1 --name sample1-svc --type=ClusterIP --port=3000
kubectl expose deploy sample-2 --name sample2-svc --type=ClusterIP --port=3000
kubectl expose deploy sample-3 --name sample3-svc --type=ClusterIP --port=3000
kubectl expose deploy sample-4 --name sample4-svc --type=ClusterIP --port=3000
These commands will create four Services with ClusterIP type for each of the sample Deployments.

Create Ingress resource
Now that you have created the Services, you can create an Ingress resource to route traffic to them based on different paths. To create the Ingress resource, run the following command:

kubectl apply -f ingress-resource.yaml
This will create an Ingress resource with rules to route traffic to the sample Services based on different paths.