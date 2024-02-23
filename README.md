# Project Overview:

Implemented a comprehensive Jenkins Pipeline to automate the Continuous Integration (CI) and Continuous Deployment (CD) process for a Java based application. 
The pipeline leverages various tools, including Git, GitHub,Docker, Maven, SonarQube, Argocd and Kubernetes, to ensure seamless code delivery from development to production environments.


The process is as follows:

Continuous Integration:
— — — — — — — — — — — — — -

1. Git Repo consists of source code for the SpringBoot application. Any commit/changes that happen here will be triggered to Jenkins .

2. As we are using Java application, we use Maven to build the application. If it is a success, it will move to the next stage.

3. Code Analysis is done through Sonarqube. It will check for code vulnerabilities and if it does have one, will send an alert to the user through email. If it does not, then it will move to the next step: Docker.

4. Here, Docker is used for building the docker image. This image will be saved in Dockerhub. If it is a success, it will move to the next step: Continuous Deployment. If it fails, then Jenkins will send an alert to the user and the pipeline ends there.

Continuous Deployment:
— — — — — — — — — — — — — —

1. The CD will get to know that the image is updated in the Docker Hub. As a new image is updated, the new version is updated in the manifests folder’s deployment.yml file.

2. Argo CD is a Kubernetes controller, responsible for continuously monitoring all running applications and comparing their live state to the desired state specified in the Git repository. Whenever there is a change, ArgoCD will pick those changes and deploy the application in the Kubernetes cluster.
