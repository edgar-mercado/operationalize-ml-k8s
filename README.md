[![edgar-mercado](https://circleci.com/gh/edgar-mercado/operationalize-ml-k8s.svg?style=svg)](https://app.circleci.com/github/edgar-mercado/operationalize-ml-k8s/pipelines)

## Project Overview

This project shows how to operationalize a Machine Learning Microservice API given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. The project will help to pass one of the assignments in the DevOps nano-degree.

### Requirements
- Linux/OSX
- Kubernetes
- Port 8000 available

### Steps to run the project

In a terminal execute the following commands
* Clone the repository `git clone git@github.com:edgar-mercado/operationalize-ml-k8s.git`
* Deploy in kubernetes `./run_kubernetes.sh`
* Open a new terminal and execute the following command to make a prediction `./make_prediction.sh`

### Content description
- `Makefile` used to run tasks like setting up the python environment, install  dependencies and lint tests.
- `Dockerfile` contains the specifications to create a Docker image of the project.
- `app.py` this is the main python program to execute or predictions, it enables two endpoints `/` and `/predict`
- `make_prediction.sh` this shell script makes a curl request to the endpoint `/predict` in the localhost to make a prediction with some sample data.
- `requirements.txt` contains the list of dependencies needed to run the python program.
- `run_docker.sh` builds the docker image with the tag `udacity-ml`, then list the images and run the container exposing the service in the host port 8000.
- `run_kubernetes.sh` pulls the image `ecme820721/udacity-ml` from DockerHub and deploys it in the kubernetes cluster, then it gets the pod name to forward the service to port 8000 in the host.
- `upload_docker.sh` push the docker image to DockerHub
- `.circleci/config.yml` contains the configuration to test our project using CircleCI
