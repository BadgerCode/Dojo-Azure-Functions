[Back To Mini Platform](/Tutorials/1-Mini-Platform/README.md)

---

# Mini Platform: Generating More Messages (Timer Trigger)

![Platform diagram](/Images/tutorials-1-mini-platform.png)

## Helpful Links
* [Create a timer triggered function](https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-scheduled-function)
* [Timer triggered function & service bus](https://docs.microsoft.com/en-us/sandbox/functions-recipes/service-bus#using-icollector-with-service-bus-queue-bindings)

## Overview
Using the functions you have created so far as examples
1. Create a timer trigger function
2. Add a service bus output binding to the middle queue
```cs
[ServiceBus("middle", Connection = "ServiceBusConnection", EntityType = EntityType.Queue)] ICollector<BrokeredMessage> queueCollector
```
3. Test it!
