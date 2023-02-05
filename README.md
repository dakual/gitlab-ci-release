docker run --rm -v $(PWD)/app:/app -w /app node:8.11-alpine npm init -y 
docker run --rm -v $(PWD)/app:/app -w /app node:8.11-alpine npm install express
docker run --rm -v $(PWD)/app:/app -w /app node:8.11-alpine npm install mocha chai chai-http --save-dev

docker run --rm -v $(PWD)/app:/app -w /app -p 8080:8080 node:8.11-alpine npm start