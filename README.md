# Kubernetes Setup Using Ansible and Vagrant

## Overview
The aim of this project is having a one line command for lifting a kubernetes cluster in your local machine fully provisioned. This is also easily extensible for installing your own stuff using Ansible.

The seed for this project was an blog post that was published during 2019 in https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/ that didn't work nowdays so it needed some affection for bringing it back to life.

## Why not using Kind or minikube or any other lightweight way of running k8s for testing purposes?
Because of when using vagrant you can choose the underlying SO and for my own experience this allow you testing stuff under the most similar conditions that would run in your production clusters. Am I advising against Kind or similar? Not at all, if you want to try some services in a kubernetes cluster is almost sure you will be fine using Kind or similar but there are other cases where you need to have more control over your hosts running k8s.

## Getting started
* `vagrant up`
* `export KUBECONFIG=./kubernetes-setup/output/config`
* `kubectl cluster-info`
* enjoy!

## Extras

* `ansible-playbook kubernetes-setup/cert-manager.yaml` for installing cert-manager
* `ansible-playbook kubernetes-setup/kubernetes-dashboard.yaml` for installing official k8s dashboard

### kubernetes dashboard
* `kubectl proxy`
* visit `http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/overview?namespace=kubernetes-dashboard`
* use the token place in `kubernetes-setup/output/token`

### Local docker registry
#### In your host
* `docker run -d -p 5000:5000 --restart=always --name registry registry:2`
* modify your `/etc/hosts` file to include `127.0.0.1 localregistry.local`
* `docker push localregistry.local:5000/<img>:<tag>`

The cluster is prepared to pull images from `localregistry.local`
## TODO
* Roles becoming idempotent