# eh-tech-exercise

Kubernetes technical exercise for Everyly Health


Install minikube:
	curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
	sudo install minikube-linux-amd64 /usr/local/bin/minikube

Start minikube:
	minikube start

Enable Ingress controller:
	minikube addons enable ingress

Verify NGINX Ingress controller is running:
	kubectl get pods -n ingress-nginx


Create an app deployment using an example image that returns "Hello, world!":
	kubectl create deployment web --image=gcr.io/google-samples/hello-app:1.0

Expose the deployment:
	kubectl expose deployment web --type=NodePort --port=8080

Create an NGINX Ingress object from nginx-ingress.yaml file:
	kubectl apply -f nginx-ingress.yaml

Verify IP address is set:
	kubectl get ingress

NAME              CLASS   HOSTS              ADDRESS        PORTS   AGE
example-ingress   nginx   hello-world.info   192.168.49.2   80      32m

Add IP address entry to /etc/hosts file:
	192.168.49.2 hello-world.info

Run curl against hello-world.info hostname to verify app is working:
	curl hello-world.info

Curl output is in curl-output.txt and log output from app pod is in log-output.txt
