[Back To Mini Platform](/Tutorials/1-Mini-Platform/README.md)

---

# Mini Platform: Creating our resources

![Platform diagram](/Images/tutorials-1-mini-platform.png)

For this platform, we will need:
* A function app
* A Service Bus namespace (this is where our queues will live)
    * Two queues- middle, output

## 1. Creating the function app
### 1.1 Create a new function using the Portal
* https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-first-azure-function
* Just create an empty function app. Don't worry about creating the HTTP trigger.

### 1.2 Create a new function project
* In Visual Studio/Visual Studio Code, create a new project for a function app
* Follow the same steps in [Your first function](/First-Steps/1.1/README.md)
    * Create an empty function app project.


## 2. Set up service bus
Service bus namespaces contain multiple service bus queues and topics. For this example, we're going to create two queues in it.

### 2.1 Create a service bus namespace
![Create service bus through the portal](/Images/service-bus-1.png)

1. Select "Service Bus" in the list of results
    * _Favourite the resource type to make it easier to find_
2. Select create and fill out the details

![Create service bus through the portal](/Images/service-bus-2.png)

### 2.2 Get your access key
Find the service bus namespace you just created.
* Using the notification in the portal
* Following the steps in [Viewing your function in the portal](/First-Steps/1.2/README.md)

#### Open up Shared Access Policies
1. Select **RootManageSharedAccessKey**
2. In the pane that opens, copy the "**Primary Connection String**".

![Retrieve service bus access key](/Images/service-bus-3.png)
![Retrieve service bus access key](/Images/service-bus-4.png)
![Retrieve service bus access key](/Images/service-bus-5.png)

<br><br>

### 2.3 Set up Service Bus Explorer

1. File -> Connect
2. "Select a service bus namespace..."
    1. Change this to "Enter connection string..."
    2. In the new box on the right "Connection String", paste the connection string you copied above.
    3. Save this connection
3. Select your connection from the "Namespace" drop down in the top-level and click ok

![Service bus explorer](/Images/service-bus-6.png)



### 2.4 Create the queues
In Azure Storage explorer, **create two queues**- one named "middle" and one named "output".

1. Connect to your namespace (see above)
2. Right click on "Queues"
3. Click Create Queue
4. Enter a name for the queue in **Relative URI**
5. Click **Create**


![Service bus explorer](/Images/service-bus-7.png)<br>
![Service bus explorer](/Images/service-bus-8.png)<br>
![Service bus explorer](/Images/service-bus-9.png)



<br><br>

---
## Next- 1.2 [Adding Messages (HTTP Trigger)](/Tutorials/1-Mini-Platform/1.2/README.md)
---