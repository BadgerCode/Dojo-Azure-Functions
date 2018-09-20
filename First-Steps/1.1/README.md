[Back home](/README.md)

---

# 1.1 Your first function

## Create a basic function
Following one of the methods below, create a new Function App.

* Using Visual Studio
    * https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-your-first-function-visual-studio
* Using Visual Studio Code
    * https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-first-function-vs-code
* In the Portal
    * https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-first-azure-function
    * _C# functions created via the portal will be created as C# Scripts. Bear in mind these work slightly differently to functions created using Visual Studio or Visual Studio Code_ - [C# Script Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-reference-csharp)

## Extra Steps
* Try to add another function to the same function app you created above
* Make some changes to your function, re-publish it to Azure and then use it
    * E.g. Change the response message from
        * `"Hello " + name`
        * to
        * `"Good afternoon " + name + "!"`


## Questions?
#### What's a resource group?
* Resource groups are a way for you to group related resources
* For example, you put all resources for a product in a single group

#### Why does my function need a "Storage Account"?
* This is where the files required to run your function live

#### What's a consumption plan/app service plan?
* A plan is basically a place for your function to run
* An **app service plan** is equivalent to renting a **fixed place** for your function and other resource to live
    * https://docs.microsoft.com/en-us/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview
* A **consumption plan** is a **dynamic place** for your function to live. Depending on load, copies of your function may be added or removed
    * https://docs.microsoft.com/en-us/azure/azure-functions/functions-scale#consumption-plan

<br><br>

---
## Next- 1.2 [Viewing your function in the portal](/First-Steps/1.2/README.md)
---