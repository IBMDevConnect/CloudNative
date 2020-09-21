# Deploying Web Application on Kubernetes

## Objective
1. Deploy an application on Kubernetes
2. Scale and Update Deployments

## Pre-requisite
1. Log in/Sign up on the Katacoda playground
2. Log in to this link : https://www.katacoda.com/courses/kubernetes/kubectl-run-containers#

#### Step 1) Launch Cluster

To start we need to launch a Kubernetes cluster.

Execute the command below to start the cluster components and download the Kubectl CLI.

```minikube start --wait=false```

Wait for the Node to become Ready by checking

```kubectl get nodes```

#### Step 2) Create the guestbook application deployment:

```kubectl create deployment guestbook --image=ibmcom/guestbook:v1```

Check the status of the running application, you can use:

```kubectl get pods```

You should see similar output O/P:
``` console
$ kubectl get pods
NAME                          READY     STATUS              RESTARTS   AGE
guestbook-87b756bd5-5dxsr     0/1       ContainerCreating   0          1m
```

It will take some time to get this pod in running state
``` console
$ kubectl get pods
NAME                              READY   STATUS    RESTARTS   AGE
guestbook-87b756bd5-5dxsr         1/1     Running   0          112m
```
#### Step 3) Expose the application
Once the status reads Running, we need to expose that deployment as a Service so that it can be accessed from outside. By specifying a service type of NodePort, the service will also be mapped to a high-numbered port on each cluster node. The guestbook application listens on port 3000, so this is also specified in the command.

```kubectl expose deployment guestbook --type="NodePort" --port=3000 --external-ip="Give the host0 IP value "```

You can get the external ip value from the Katacoda environment by clicking on the settings from the top right and then click on Debug.

Example:
``` console
$ kubectl expose deployment guestbook --type="NodePort" --port=3000 --external-ip="172.17.0.26"
service "guestbook" exposed
```
Check the service using command
``` kubectl get svc```

``` console
$ kubectl get svc
NAME         TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
guestbook    NodePort    172.21.156.20    <none>        3000:30298/TCP   101m
```

Guestbook application is exposed at port 30298(for example) on public ip of cluster

#### Step 4) Access the guestbook app

You can run the curl command to access the code of the guestbook application.

```curl http://<external-ip>:<Nodeport_port>```

eg: curl http://184.173.1.140:30298/


### Scale the application

A replica is a copy of a pod that contains a running service. By having multiple replicas of a pod, you can ensure your deployment has the available resources to handle increasing load on your application.

Step 1) To Scale the guestbook application use command

```kubectl scale --replicas=10 deployment guestbook```

O/P:
``` console
$ kubectl scale --replicas=10 deployment guestbook
deployment "guestbook" scaled
```
 Kubernetes will now try to match the desired state of 10 replicas by starting 9 new pods with the same configuration
as the first.

```console
$ kubectl rollout status deployment guestbook
Waiting for rollout to finish: 1 of 10 updated replicas are available...
Waiting for rollout to finish: 2 of 10 updated replicas are available...
Waiting for rollout to finish: 3 of 10 updated replicas are available...
Waiting for rollout to finish: 4 of 10 updated replicas are available...
Waiting for rollout to finish: 5 of 10 updated replicas are available...
Waiting for rollout to finish: 6 of 10 updated replicas are available...
Waiting for rollout to finish: 7 of 10 updated replicas are available...
Waiting for rollout to finish: 8 of 10 updated replicas are available...
Waiting for rollout to finish: 9 of 10 updated replicas are available...
deployment "guestbook" successfully rolled out
   ```

``` console
$ kubectl rollout status deployment guestbook
deployment "guestbook" successfully rolled out
```
Step 2) Check number of pods running by usig command
``` kubectl get pods```

``` console
$ kubectl get pods
NAME                              READY   STATUS    RESTARTS   AGE
guestbook-87b756bd5-5dxsr         1/1     Running   0          138m
guestbook-87b756bd5-b9vfp         1/1     Running   0          61s
guestbook-87b756bd5-ftmxn         1/1     Running   0          61s
guestbook-87b756bd5-jwsqm         1/1     Running   0          61s
guestbook-87b756bd5-l46pv         1/1     Running   0          61s
guestbook-87b756bd5-q9gk9         1/1     Running   0          61s
guestbook-87b756bd5-vnw9t         1/1     Running   0          61s
guestbook-87b756bd5-vs56p         1/1     Running   0          61s
guestbook-87b756bd5-xtwck         1/1     Running   0          61s
guestbook-87b756bd5-zbqls         1/1     Running   0          61s

```

#### Kubernetes Update and rollback
Kubernetes allows you to do a rolling upgrade of your application to a new container image. Kubernetes allows you to easily update the running image but also allows you to easily undo a rollout if a problem is discovered during or after deployment.

In the previous lab, we used an image with a v1 tag. For our upgrade, we'll use the image with the v2 tag.

Step 1) Using kubectl, you can now update your deployment to use the v2 image. kubectl allows you to change details about existing resources with the set subcommand. We can use it to change the image being used.

```kubectl set image deployment/guestbook guestbook=ibmcom/guestbook:v2```

O/P:
``` console
 kubectl set image deployment/guestbook guestbook=ibmcom/guestbook:v2
deployment.apps/guestbook image updated
```
Check Rollout status using command
``` kubectl rollout status deployment/guestbook```

```console
$  kubectl rollout status deployment/guestbook
deployment "guestbook" successfully rolled out
```
Step 2) Test the application as before, by accessing ```http://<public-IP>:<nodeport>``` and running the curl command to confirm your new code is active with version v2 in the code.


#### Rollback your application
Use command "undo" to rollback the deplyment at previous version

```kubectl rollout undo deployment guestbook```

O/P:
``` console
kubectl rollout undo deployment guestbook
deployment.apps/guestbook rolled back
```

Check the pod status using
``` kubectl get pods```

O/P:
``` console
$ kubectl get pods
NAME                              READY   STATUS        RESTARTS   AGE
guestbook-87b756bd5-4whpb         1/1     Running       0          13s
guestbook-87b756bd5-b6h6x         1/1     Running       0          13s
guestbook-87b756bd5-crh72         1/1     Running       0          9s
guestbook-87b756bd5-czjs2         1/1     Running       0          10s
guestbook-87b756bd5-dsv88         1/1     Running       0          13s
guestbook-87b756bd5-mh7xc         1/1     Running       0          13s
guestbook-87b756bd5-n2zt6         1/1     Running       0          9s
guestbook-87b756bd5-p9tbh         1/1     Running       0          13s
guestbook-87b756bd5-vmc6x         1/1     Running       0          9s
guestbook-87b756bd5-whhr8         1/1     Running       0          10s
guestbook-df976f65b-4lsgr         0/1     Terminating   0          10m
guestbook-df976f65b-82jd6         0/1     Terminating   0          10m
guestbook-df976f65b-gkf62         0/1     Terminating   0          10m
guestbook-df976f65b-jv9v7         0/1     Terminating   0          10m
guestbook-df976f65b-pf98c         0/1     Terminating   0          10m
guestbook-df976f65b-vsrfk         0/1     Terminating   0          10m
guestbook-df976f65b-x2mc7         0/1     Terminating   0          10m
guestbook-df976f65b-xxpsx         0/1     Terminating   0          10m
guestbook-df976f65b-z7tm9         0/1     Terminating   0          10m
load-generator-5fb4fb465b-rzsj2   1/1     Running       0          77m
logdna-agent-cjhjl                1/1     Running       0          47h
php-apache-79544c9bd9-cphmx       1/1     Running       0          78m
```

Run the curl command again , you will see that you again get guestbook V1 app.

#### Clean up
let's delete the application

To remove the deployment, use:

``` kubectl delete deployment guestbook```

To delete the service use

```  kubectl delete service guestbook```

We have finished checking scaling and rollout of application
