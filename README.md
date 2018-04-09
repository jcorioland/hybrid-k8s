

# Running Kubernetes in a hybrid environment

# Intro

Setting up Kubernetes in a hybrid environment imposes some requirement on the setup, and implies some considerations around how you will configure your cluster, and plan your deployments. In this guide, we will look at a typical hybrid cloud setup to deploy Kubernetes.

Note : We do not cover a Kubernetes cluster _spanning_ a hybrid cloud network, but rather how to run a cluster in the cloud and interact with an existing local network seamlessly.

# Pre-requisites

# Infrastructure

## Express Route / VPN

## Peering

## Topology

The network topology must be well defined beforehand to enable peering between the different VNET. This means that the subnet ip range musty be defined before deploying kubernetes. It cannot be changed afterwards.

## Dns

# Kubernetes

## Network

By default, acs-engine network policy is using the **azure cni** plugin. This has some advantages and some consequences that must be considered when defining the network where we deploy the cluster. CNI provides an integration with azure subnet ip addressing so that every pod created ny kubernetes is assigned an ip address from the corresponding subnet.

Consequences:

- --Subnets where you deploy Kubernetes must be sized according to your scaling plan
- --You must account for Kubernetes components
- --Network Security must be applied at the subnet level, using Azure NSG
- --No masquerading happens on outgoing network calls (packets origin are the pod ip, not the node ip)

## Services

## Devops

# Conclusion

