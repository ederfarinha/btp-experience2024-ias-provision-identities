# Getting started

Before starting with the exercises, let us have a short reminder of what the SAP Cloud Identity Services are. 


   
<img align="right" width="650" src="/exercises/ex0/images/SCI.png" />

SAP Cloud Identity Services (SCI) are the default to authenticate and provision users in cloud solutions from SAP:
* Identity authentication (IAS)
* Identity provisioning (IPS)
* Authorization management (AMS)
* Integrated through the common Identity Directory (IdDS)

The number of **pre-integrated SAP solutions** that require **SAP Cloud Identity Services** will increase.
There is no need to separately license the usage of our services, when used with SAP cloud solutions. 
**By default**, we offer **two SCI tenants**: 
* Test tenant
* Production tenant

**What is Identity authentication?**
The Identity Authentication service provides you with controlled cloud-based access to business processes, applications, and data. It simplifies your user experience through authentication mechanisms, single sign-on, on-premise integration, and convenient self-service options.

**What is Identity Provisioning?**
The Identity Provisioning service automates identity lifecycle processes. It helps you provision identities and their authorizations to various cloud and on-premise business applications.

**What is Authorization Management?** 
Authorization management provides a central management of end-user authorizations for business applications based on SAP BTP Technology Platform. AMS is based on the existing Identity Directory of SAP Cloud Identity Services and enables customers to manage assignments of policies to users based on the Identity Directory SCIM API.

**What is the Identity Directory?**
Identity Directory is the central component for persisting users and groups inside the SAP Cloud Identity Services.
The usage of the Identity Directory simplifies how customers are connecting to our SAP SaaS applications, by using it as a central point of truth for the SAP cloud environment. 
Additionally to the SAP Cloud Identity Services admin console UI, a SCIM 2.0 API allows you to programmatically access the identities inside the directory.

For more information around these services, feel free to explore our [SAP Cloud Identity Services](https://help.sap.com/docs/cloud-identity) documentation as well as our [API collection](https://api.sap.com/package/SCPIdentityServices/rest) published on the SAP API Business Accelerator hub . All the services can be visually interacted with from the SAP Cloud Identity Services admin console.   

## Hands-on scenario
To better understand the provisioning functionality available in the SAP Cloud Identity Service, we will go together through the next exercises. The scenario is chosen in such a way that it resembles albeit at small scale the identity lifecycle in a landscape. We will start by connecting a user source to the Identity Provisioning. For this, we will use a SAP SuccessFactors Systems. Afterwards, we will configure a target system - the Identity Directory. We will go through the different job types and learn how to change the default IPS transformations and how to validate their behavior.

## Accessing the SAP Cloud Identity Services tenant

Now that we know what the SAP Cloud Services are and we understood what the scope of this hands-on session is, let us check the system access. For this session you will need access to a SAP Cloud Identity Service (SCI) tenant and a SAP SuccessFactors instance. 

1. Search for the internet browser on your computer and navigate to your SCI administrative console.

The SAP Cloud Identity Service tenant URL is specific for your seat in the workshop room.  

URL: https://aruagcnbn.accounts.ondemand.com/admin    


2. Type the username and password and press **Log On**

   <img src="/exercises/ex0/images/02.png" width=50% height=50%>

3. You have access to the SAP Cloud Identity Services administrative console.
   
   <img src="/exercises/ex0/images/01.png" width=50% height=50%>
   

   



## Summary

Now that you have logged in your SCI console, continue to - [Exercise 1 - Exercise 1 Description](../ex1/README.md)
