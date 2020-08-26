# Working with OpenShift operators to deploy a database on Red Hat OpenShift on IBM Cloud

### Pre-requisite: Create IBM Cloud Account [IBM Cloud](https://cloud.ibm.com/registration). Please register with your Organization Email ID.

## IBM Cloud Login

Start by opening a web browser and navigating to [IBM Cloud](https://cloud.ibm.com/).

![Cloud Login](images/Cloud-Login.png)

Next **_login_** with your IBM Cloud login you created. After login you will be navigated to your **Cloud Dashboard**.

![IBM Cloud Dashboard](images/IBM_Cloud_Dashboard.png)

#### Step 1. Find the community operator

Begin by switching to the administrator mode in OpenShift and browse to the OperatorHub. In the navigation, expand **Operators** and select **OperatorHub**:

![Cloud Login](images/pg-openshift-operator-1.png)

Then search for **PostgreSQL** in the OperatorHub and click the Install button to install the **Dev4Devs community PostgreSQL operator**:

![Cloud Login](images/pg-openshift-operator-2.png)

### Step 2. Subscribe to an operator

Now you need to select one your existing namespaces where you want to install the operator. This is the namespace where you can create instances of the database:

![Cloud Login](images/pg-openshift-operator-3.png)

After you have installed an operator by subscribing to one of the channels to keep it up-to-date, you can view installed operators. In the navigation, under **Operators** select **Installed Operators**. Now you see the PostgreSQL operator:

![Cloud Login](images/pg-openshift-operator-4.png)

### Step 3. Switch to the Developer view and create the database

Change your view from Administrator to Developer and select **Topology** to view your deployed operator.

Click on **+Add** link in the left hand panel and then select the Database tile, as shown in the following screen capture:

![Cloud Login](images/pg-openshift-operator-6a-dev.png)

Next, in the developer catalog, select the Postgres **Database Database** tile for your operator:

![Cloud Login](images/pg-openshift-operator-6b-dev.png)

Here you can select the size of the volume assigned to the database, as well as resource limits for the database. You can also specify the database name and namespace: for example, call the name creditdb and call the namespace example-bank, as shown in the following screen capture:

![Cloud Login](images/pg-openshift-operator-6c-dev.png)



**Congratulations on successfully building and deploying application on IBM Cloud**
