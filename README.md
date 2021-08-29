# Kubernetes Setup Using Ansible and Vagrant

## Overview
The aim of this project is having a one line command for lifting a kubernetes cluster in your local machine fully provisioned. This is also easily extensible for installing your own stuff using Ansible.

The seed for this project was an blog post that was published during 2019 in https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/ that didn't work nowdays so it needed some affection for bringing it back to life.

## Why not using Kind or minikube or any other lightweight way of running k8s for testing purposes?
Because of when using vagrant you can choose the underlying SO and for my own experience this allow you testing stuff under the most similar conditions that would run in your production clusters. Am I advising against Kind or similar? Not at all, if you want to try some services in a kubernetes cluster is almost sure you will be fine using Kind or similar but there are other cases where you need to have more control over your hosts running k8s.

## Getting started
* vagrant up
* export KUBECONFIG=./kubernetes-setup/output/config
* kubectl cluster-info
* enjoy!

## TODO
* Roles becoming idempotent