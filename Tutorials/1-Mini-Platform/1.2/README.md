[Back To Mini Platform](/Tutorials/1-Mini-Platform/README.md)

---

# Mini Platform: Adding Messages (HTTP Trigger)

![Platform diagram](/Images/tutorials-1-mini-platform.png)

## Helpful Links
* [Service bus output binding](https://docs.microsoft.com/en-us/sandbox/functions-recipes/service-bus#using-icollector-with-service-bus-queue-bindings)

## 1. Create the HTTP trigger
Create a new function in your function app project.
* Use Anonymous for the Authorization level

## 2. Add the service bus connection string
1. Open up **local.settings.json** in your function app project
2. Add an entry for **ServiceBusConnection** like so:
```json
{
    "IsEncrypted": false,
    "Values": {
        "AzureWebJobsStorage": "UseDevelopmentStorage=true",
        "AzureWebJobsDashboard": "UseDevelopmentStorage=true",
        "ServiceBusConnection": "Endpoint=sb://a-unique-name.servicebus..."
    }
}
```

## 3. Install the ServiceBus package
`Microsoft.Azure.WebJobs.ServiceBus`

## 4. Update the function code for your HTTP trigger
1. This code will take a HTTP POST request
2. Split the body into lines
3. Add each line as a message on the "middle" queue


Usings at the top:
```cs
using System.Net;
using System.Net.Http;
using System.Threading.Tasks;
using Microsoft.Azure.WebJobs;
using Microsoft.Azure.WebJobs.Extensions.Http;
using Microsoft.Azure.WebJobs.Host;
using Microsoft.Azure.WebJobs.ServiceBus;
using Microsoft.ServiceBus.Messaging;
```

Run method
```cs
[FunctionName("Function1")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Anonymous, "post", Route = null)]
    HttpRequestMessage req,
    [ServiceBus("middle", Connection = "ServiceBusConnection", EntityType = EntityType.Queue)] ICollector<BrokeredMessage> queueCollector,
    TraceWriter log)
{
    log.Info("C# HTTP trigger function processed a request.");

    var body = await req.Content.ReadAsStringAsync();

    var lines = body.Split('\n');

    foreach (var line in lines)
    {
        queueCollector.Add(new BrokeredMessage(line));
    }

    return req.CreateResponse(HttpStatusCode.OK, "Sent " + lines.Length + " lines");
}

```


## 5. Test the function
Using Postman, send a POST request to your function URL.

![Postman](/Images/1-mini-platform-test-http.png)
![Postman](/Images/1-mini-platform-test-http-0.png)
![Postman](/Images/1-mini-platform-test-queue.png)


<br><br>

---
## Next- 1.3 [Processing Messages (Queue Trigger)](/Tutorials/1-Mini-Platform/1.3/README.md)
---