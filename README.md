# capsule-multi-tenancy

Table of Contents
-
* [Introdution](#intro)
* [Pre-Requisites](#req)
* [Installation](#install)


<a name="intro"></a>Introduction
-
Follow the steps to setup to setup Multi-Tenancy for Kubernetes cluster using [Capsule](https://capsule.clastix.io/).

<a name="req"></a>Pre-Requisites
-
0. [Local Kubernetes Setup](#K8s)
0. [kubectl](#kubectl)
0. [helm](#helm)
0. [openssl](#openssl)

For the installation of Requirements listed above, follow the steps and run the following commands in terminal:

0. <a name="K8s"></a> Local Kubernetes Setup <br />
          MiniKube:- https://minikube.sigs.k8s.io/docs/start/ <br />
          K3d :- https://k3d.io/v5.4.6/ <br />
          Kind :- https://kind.sigs.k8s.io/docs/user/quick-start/ <br />

0. <a name="kubectl"></a>kubectl

        Kubectl setup :- https://kubernetes.io/docs/tasks/tools/
        
0. <a name="helm"></a>helm

       Helm Setup :- https://helm.sh/docs/intro/install/
         
0. <a name="openssl"></a>openssl
    Openssl Install :- https://www.openssl.org/
    
<a name="install"></a>Installation

-

1. Add this repository:

        $ helm repo add clastix https://clastix.github.io/charts

2. Install the Chart:

        $ helm install capsule clastix/capsule -n capsule-system --create-namespace

3. Show the status:

        $ helm status capsule -n capsule-system
        

4. Apply tenant manifest file:

        $ cat tenant.yaml
        $ kubectl apply -f tenant.yaml
5. Create user and certificates:

        $ ./create-user.sh <user> <team-name>
6. Export Kubeconfig created in setup 5:

        $ export KUBECONFIG=<user>-<team-name>.kubeconfig
7. Create namespace:

        $ kubectl create ns <namespace>
