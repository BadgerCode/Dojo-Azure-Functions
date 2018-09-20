[Back To Mini Platform](/Tutorials/1-Mini-Platform/README.md)

---

# Mini Platform: Processing Messages (Queue Trigger)

![Platform diagram](/Images/tutorials-1-mini-platform.png)

## 1. Create the queue trigger
* Use the same function app as before

## 2. Add the queue message handler code
```cs
using Microsoft.Azure.WebJobs;
using Microsoft.Azure.WebJobs.Host;
using Microsoft.Azure.WebJobs.ServiceBus;
using Microsoft.ServiceBus.Messaging;
```

```cs
[FunctionName("Function2")]
public static void Run([ServiceBusTrigger("middle", AccessRights.Manage, Connection = "ServiceBusConnection")]
    string myQueueItem, 
    [ServiceBus("output", Connection = "ServiceBusConnection", EntityType = EntityType.Queue)] ICollector<BrokeredMessage> queueCollector,
    TraceWriter log)
{
    log.Info($"C# ServiceBus queue trigger function processed message: {myQueueItem}");

    queueCollector.Add(new BrokeredMessage(myQueueItem));
}
```

## 3. Test it
* Use the HTTP trigger you previously made to generate some queue messages
* Messages should end up on the output queue

![Postman](/Images/1-mini-platform-test-queue.png)

### Test it live
When deploying this to Azure, you will need to add an application setting in the portal.
1. Find your function in the portal
2. Open up the interface for the function
3. Open "Application Settings"
4. Add a setting with **ServiceBusConnection** and the service bus connection string as the value



<br><br>

---
## Next- 1.4 [Generating More Messages (Timer Trigger)](/Tutorials/1-Mini-Platform/1.4/README.md)
---