minikube delete --all --purge
minikube start --driver=docker

docker pull nginx
minikube image load nginx

kubectl create deployment demokube --image=nginx
kubectl get deployments
kubectl get pods

kubectl scale deployment demokube --replicas=4
kubectl get pods

kubectl expose deployment demokube --type=NodePort --port=80
kubectl get svc demokube

minikube service demokube --url

kubectl delete service demokube
kubectl delete deployment demokube

minikube stop
minikube delete --all --purge










groovy script pipeline

---------------------
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building the project..."
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying..."
            }
        }
    }
}
-----------------
nagios
-------------

docker pull jasonrivers/nagios:latest
docker run --name nagiosdemo -p 8888:80 jasonrivers/nagios:latest
open browser and enter localhost://8888
Username: nagiosadmin
password: nagios

docker stop nagiosdemo
docker rm nagiosdemo
-------------------------------------





AWS DEPLOYMENT COMMANDS (SHORT NOTES FOR EXAM)
-------------------------------------------
# Upload project to EC2
scp -i key.pem -r myapp/ ec2-user@EC2_IP:/home/ec2-user/

# SSH into EC2
ssh -i key.pem ec2-user@EC2_IP

# Start application
cd myapp
npm install
node app.js


# Create bucket
aws s3 mb s3://mybucket

# Upload files
aws s3 sync . s3://mybucket

# Enable website hosting
aws s3 website s3://mybucket --index-document index.html


# Create ZIP
zip -r app.zip .

# Upload to Lambda
aws lambda update-function-code \
--function-name myFunction \
--zip-file fileb://app.zip

# Login to ECR
aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin ACCOUNT_ID.dkr.ecr.ap-south-1.amazonaws.com

# Build + Tag
docker build -t myapp .
docker tag myapp:latest ACCOUNT_ID.dkr.ecr.ap-south-1.amazonaws.com/myapp:latest

# Push
docker push ACCOUNT_ID.dkr.ecr.ap-south-1.amazonaws.com/myapp:latest
aws ecs update-service \
--cluster myCluster \
--service myService \
--force-new-deployment
eb init
eb create my-env
eb deploy

# AWS
ssh-i...........com
sudo apt update 
sudo apt-get install docker.io
sudo apt install nano

#Add pairkeyfile in AWS folder
#create index.html and write code
#push it in GitHub

git clone https://............AWS.git
ls
cd AWS
ls


#(past)->FROM nginx:alpine
COPY . /usr/share/nginx/html

sudo docker build -t mywebapp
sudo docker run -d -p 80:80 mywebapp

# go to instances-> copy public ipv4 address->run it in browser

sudo docker ps 
sudo docker stop (container_id)

#terminate 

#Maven
ssh-i...........com
sudo apt update 
sudo apt-get install docker.io
sudo apt install git
sudo apt install nano

#push it in GitHub

git clone https://............AWS.git
ls
cd MavenWebProject
ls
nano Dockerfile
sudo docker build -t mavenwebproject .
sudo docker run -d -p 9090:8080 mavenwebproject .

# go to instances-> security->inbound rules->add custom TCP and port range:9090-> copy public ipv4 address ->past in browser.

sudo docker ps
sudo docker stop (container_id)

#terminate
