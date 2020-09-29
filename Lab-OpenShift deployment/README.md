# Deploying a front end and backend application on OpenShift 

Learn how to deploy an application (the ParksMap front end) from a pre-existing container image along with learn how to deploy an application direct from source code hosted in a remote Git repository.
This will be done using the Source-to-Image (S2I) tool.

## Pre-requisites

* [IBM Cloud account](https://cloud.ibm.com/)
* [OpenShift CLI](https://cloud.ibm.com/docs/openshift?topic=openshift-openshift-cli)

## Steps

1. Logging into an evironment provided by your trainer, so that you can avail an OpenShift cluster.
2. Logging in with the Web Console
3. Creating a Project
4.  Deploying Your First Image
5. Scaling Your Application
6. Routing HTTP Requests
7. Building From Source Code

## 1. Logging into an evironment provided by your trainer, so that you can avail an OpenShift cluster.

Log in to the [Interactive Learning Portal](https://learn.openshift.com/introduction/getting-started/)

## 2. Logging in with the Web Console

To begin, click on the Console tab on your screen. This will open the web console on your browser.
You should see a Red Hat OpenShift Container Platform window with Username and Password forms as shown below:

![OCP login page](doc/source/images/pic1.png)

Use the crededntials provided by the workshop trainer to login here.

## 3. Creating a Project

OpenShift is often referred to as a container application platform in that it is a platform designed for the development and deployment of applications in containers.
To group your application, we use projects. The reason for having a project to contain your application is to allow for controlled access and quotas for developers or teams.
More technically, it's a visualization of the Kubernetes namespace based on the developer access controls.

Click the blue Create Project button.
You should now see a page for creating your first project in the web console. 
Fill in the Name field as 'myproject'

![Project creation](doc/source/images/pic2.png)
 
The rest of the form is optional and up to you to fill in or ignore. Click Create to continue.

After your project is created, you will see some basic information about your project.

## 4.  Deploying Your First Image

Notice the navigation menu on the left. When you first log in, you'll typically be in the Administrator Perspective.
If you are not in the Administrator Perspective, click the perspective toggle and switch from Developer to Administrator.

![Developer view](doc/source/images/pic3.png)
 
**You are going to deploy the front end component of an application called parksmap. The web application will display an interactive map, which will be used to display the location of major national parks from all over the world.**

## 5. Scaling Your Application

## 6. Routing HTTP Requests

## 7. Building From Source Code
