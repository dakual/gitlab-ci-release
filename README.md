docker run --rm -v $(PWD)/app:/app -w /app node:8.11-alpine npm init -y 
docker run --rm -v $(PWD)/app:/app -w /app node:8.11-alpine npm install express
docker run --rm -v $(PWD)/app:/app -w /app node:8.11-alpine npm install mocha chai chai-http --save-dev

docker run --rm -v $(PWD)/app:/app -w /app -p 8080:8080 node:8.11-alpine npm start



kubectl create secret docker-registry registry-key \
  --docker-server=registry.gitlab.com \
  --docker-username=dakual \
  --docker-password=glpat-Xk3sXBnoMAcDZPReqQM5

kubectl create secret docker-registry registry-key \
--docker-server=registry.gitlab.com \
--docker-username=minikube \
--docker-password=UUXq1BFw1zy4JpTysMsL \
--namespace=dev


kubectl get secret registry-key --namespace=default -o yaml | grep -v '^\s*namespace:\s' | kubectl apply --namespace=dev -f -
kubectl get secret registry-key --namespace=default -o yaml | grep -v '^\s*namespace:\s' | kubectl apply --namespace=staging -f -
kubectl get secret registry-key --namespace=default -o yaml | grep -v '^\s*namespace:\s' | kubectl apply --namespace=prod -f -