# Build a Cloud Native App with Automated DevOps from a Starter Kit

### Pre-requisite: Create IBM Cloud Account [IBM Cloud](https://ibm.biz/BdqAuc). Please register with your Organization Email ID.

## IBM Cloud Login

Start by opening a web browser and navigating to [IBM Cloud](https://cloud.ibm.com/).

![Cloud Login](images/Cloud-Login.png)

Next **_login_** with your IBM Cloud login you created. After login you will be navigated to your **Cloud Dashboard**.

![IBM Cloud Dashboard](images/IBM_Cloud_Dashboard.png)

#### Create Kubernetes Cluster

From the catalog, navigate to Kubernetes Cluster and Select the Kubernetes Service

![Cloud Login](images/First.png)

Select the free plan, give a name to the cluster and click on create

![Cloud Login](images/Second.png)

From the catalog, navigate to Java Spring App

![Cloud Login](images/Third.png)

Provide a name to the application and click on create

![Cloud Login](images/Fourth.png)

After the app is created, click on **Deploy your app**

![Cloud Login](images/Fifth.png)

Select the Kubernetes Service to deploy the app and click on **new** to create the API Key

![Cloud Login](images/Sixth.png)

Click on **OK** to create the API key

![Cloud Login](images/Seventh.png)

Select the appropriate region and your cluster to deploy the application and click on **Next**

![Cloud Login](images/eighth.png)

You can see the build, containerize and deploy stage running. Click on **View logs and history** to get the URL of the application

![Cloud Login](images/ninth.png)

At the bottom, click on the URL **View the Application At**  

![Cloud Login](images/tenth.png)

If the application is successfully deployed, you should get the below output

![Cloud Login](images/output.png)

Let us make some changes in the code and redeploy our application. For making changes in the code, please follow the below steps

Click on the name of the application from the App details page as shown below

![Cloud Login](images/appinfo.png)

Select the Eclipse Orion Web IDE tile to edit the code

![Cloud Login](images/codeide.png)

Open the index.html file and edit the code

![Cloud Login](images/code.png)

Once the code changes are done, select the Git icon from the left navigation

![Cloud Login](images/Git.png)

Enter the commit message and click on **commit**. Post commit is done, click on **sync**

![Cloud Login](images/commit.png)

The Delivery Pipeline gets triggered and initially we will see the Build stage running again

![Cloud Login](images/build.png)

Once the Build, Containerize, Deploy stages have completed running, we can access the newly deployed application by clicking on **View logs and history**

![Cloud Login](images/ninth.png)

At the bottom, click on the URL **View the Application At**  

![Cloud Login](images/tenth.png)

If the application is successfully deployed, you should get the below output

![Cloud Login](images/changeoutput.png)

**Congratulations on successfully building and deploying application on IBM Cloud**
