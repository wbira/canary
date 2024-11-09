start-minikube:
	minikube start
	minikube addons enable ingress

ns:
	kubectl create namespace canary-demo

setup-prometheus:
	helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
	helm repo update
	helm install prometheus prometheus-community/kube-prometheus-stack -n canary-demo

install:
	helm install canary-demo ./canary-demo -n canary-demo

deploy:
	helm upgrade canary-demo ./canary-demo -n canary-demo

get-resources:
	kubectl get pod,svc,deployments -n canary-demo -o wide

get-service-pods:
	kubectl get pods -n canary-demo -l 'app in (canary-demo,canary-demo-canary)' -o wide

test:
	python ./tests/test_app.py




