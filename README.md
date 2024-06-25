# hello-K8s
This Repository aims to hold the files needed to create a simple Hello World K8s application and deployment phases of the application. the files are as followed: 

Docker Image Files : 
hello.py : the python file of the image. 
dockerfile : the docker file to build the docker image.

K8s Files : 
- deploy.yml : the deployment file that deploys the docker image , where i specified the ressource requests and limits, liveness and readiness probes.
- service.yml : the service file with a loadbalancer type.
- ingress.yml : the ingress file that configures an the Ingress controller.
- HPA.yml : the HPA file that configures Horizontal Pod Autoscaler and automatic escalation. 
- policy.yml : the network policy file to configure traffic restriction to the application.

Phase 1 : Build the docker image 
- for this phase we will need a docker engine and for that we used the Docker Desktop application. 
- After creating the hello.py file and the docker file we will build the image in the Docker Hub by running the commands :
    docker build -t hanuch556/helloimage .
    docker push hanuch556/hello-world-python
  (before build the image we need to login first)
- After building the image we can see the image in the docker hub account repo and we can make it public .

Phase 2 : Deploy the Kubernets application
- in this phase we will apply the Yaml files that were created before by using the following command: kubectl apply -f --filename--
- to see the deployment type : kubectl get deploy , it will display the "hello2" deployement.
- to verify the pod type : kubectl get pods , it will display the pod that was created based on the image that we pushed to the 
- to verify the automatic escalation try deleting the pod that were showen in the previous command by typing : kubectl delete pod --pod name-- ==> you will see that a new pod is created in the same deployment.

