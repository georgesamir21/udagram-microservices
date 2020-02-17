# Udacity Project - Refactor Udagram Into Microservices

Refactoring [udagram initial monolitic](https://github.com/udacity/cloud-developer/tree/master/course-02/exercises/udacity-c2-restapi) application into separate microservices as follows:


- Divide the application into smaller services and extend it with additional service and automatic continuous integration and continuous delivery.
- Containerize the application, create the Kubernetes resource and deploy it to a Kubernetes cluster.
- Extend the application with deployments and be able to do rolling-updates and rollbacks.

## Usage
### Installation
- Prerequisite: It is best to have Ubuntu 18.04, Docker 18.09, KubeOne v0.9.0, Terraform 0.12.8 installed before starting the project.
- Once the repository has been downloaded, you will need to first install all dependencies by running `npm i`. You will need to repeat this for all `Frontend`, `Restapi-Feed` and `Restapi-user` folders.
- Also, ensure all environment variables are set up in your `~/.profile`.
- For Docker:
    - First, install Docker in your system.
    - Build images using `docker-compose -f docker-compose-build.yaml build --parallel`
    - Push the docker images to DockerHub using `docker-compose -f docker-compose-build.yaml push`.
    - Run application locally using `docker-compose -f docker-compose.yaml up`. **Note** you have to export enviroment varibales needed for the application first. Fill *secrets.example.sh* and Run `source secrets.example.sh`
    - Go to Localhost:8100 to test. 
    - Docker deployment complete.
- For Kubernetes:
    - Install Kubernetes using the Kubeone instructions given here:  `https://github.com/kubermatic/kubeone/blob/master/docs/quickstart-aws.md`
    - Follow the setup videos closely, and export the KubeConfig.
    - Check for the proper setup using `kubectl get pods`.
    - Set up the secret keys and configmaps for the project. These are the .yaml files in the k8s folder.
    - Make sure the .yaml files are also pointing to the right Docker images which you set up previously.
    - Use `kubectl apply -f [file-name]` on the secret key, config map files.
    - Use `kubectl apply -f [file-name]' again for the remaining .yaml files. If all is set up correctly, you will see all pods running. Test using `kubectl get rs`, `kubectl get deployment`, and `kubectl get pods`.
    - Forward the deployment port to Localhost:8080 using `kubectl port-forward [name]/reverseproxy-[id] 8080:8080`.
    - Go to Localhost:8080 to test. 
    - Kubernetes deployment completed.
- For Travis:
    - Ensure your Github account is linked to Travis. This is done via signing up for a Travis account, then from within linking the two together.
    - Push your folders to Github repository. No need for node_modules nor secrets to be included in the repository. 
    - Ensure the .travis.yml file is in the root folder of the Github repo. 
    - Go to Travis, then search for the repository, and then set up new build.
    - Travis deployment completed.

## Dependencies

There are dependencies on having an S3 bucket provisioned and an RDS postgres instance provisioned if you want to run this locally on your machine

### Images for evidence
- Attached are the following images which demonstrate the functionality of the project:
    - Running application;
    - DockerHub images;
    - Kubernetes running pods; and
    - Travis deployment completed.