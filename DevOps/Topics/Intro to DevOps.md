# Intro to DevOps

## What is DevOps
DevOps is a combination of Development(Dev) and operations(Ops) team being put together, to increase the efficiency, speed and security of software development.

## DevOps Environments
- *DEV*: development environment where features are build and tested loosely to check if the feature is functional.
- *TEST*: an environment that simulates the prod environment and various checks are carried out before the feature is pushed out.
- *PROD*: in this environment , the site is live and users can interact with the newly implemented features.

## DevOps Pipeline
5 stages of the pipeline:
- Build (the software)
- Test (the software)
- Package (the software)
- Deployment (on the prod environment)
- Validation (check if it's working as intended)

## DevOps Tools
SCM (Source Control Manager)
- Git , Bitbucket
- Keep a record of code changes and enable collobration between team members.
CI (Continuous integration) and automation servers
- Jenkins , Team City and Circle CI
- Build and test code , automate tasks and create pipelines for deployment
Automated Deployments
- FluxCD , Puppet, Chef
- Automate deployment
Cloud
- AWS, Azure
- Cloud storage available without the hardware cost.
Orchestration
- Ansible, puppet, terraform
- create environment, provision hosts and services.
Containers 
- Docker
- package the application with all its dependencies, also known as microservice.
Container Service
- Kubernetes
- Solution to manage multiple containers
Monitoring
- Grafana, Prometheus
- Observe and monitor the system health with metrics, logs , events and thresholds for alerts.