[Back home](/README.md)

---

# Mini Platform Tutorial
Now we're going to get our hands dirty and play around with 
* Different types of triggers
* Storage accounts
* Queues
* Connecting functions to eachother

## Overview
![Platform diagram](/Images/tutorials-1-mini-platform.png)

### 1. Messages are added to the middle queue **"Middle" Queue**
* HTTP requests can add one or more messages
* A timer creates a message with the current time
### 2. These will then be processed before finally being added to the **"Output" Queue**

# Steps
* _If you're short on time you can skip the trigger step_
* _You can do the timer trigger first instead of the HTTP trigger_

## 1.1 [Creating our Resources](/Tutorials/1-Mini-Platform/1.1/README.md)
## 1.2 [Adding Messages (HTTP Trigger)](/Tutorials/1-Mini-Platform/1.2/README.md)
## 1.3 [Processing Messages (Queue Trigger)](/Tutorials/1-Mini-Platform/1.3/README.md)
## 1.4 [Generating More Messages (Timer Trigger)](/Tutorials/1-Mini-Platform/1.4/README.md)