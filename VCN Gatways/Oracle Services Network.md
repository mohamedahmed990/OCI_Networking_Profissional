

### **Introduction to the Oracle Services Network**

*   The Oracle Services Network.
*   This is a very important topic.
*   And it's outside of your virtual cloud networks.
*   But the Oracle Services Network exists even beyond your tenancy.
*   It's a set of resources that you can leverage or you cannot leverage.
*   But if you do, then you will need a service gateway.
*   And we'll get to that on future lessons.
*   Now let's go ahead and concentrate on the Oracle Services Network.
*   My name's Sergio Castro with Oracle University.
*   And thank you for joining.
*   Let's go ahead and get started.

### **1. What is the Oracle Services Network?**

*   So the Oracle Services Network sits on OCI.
*   Basically, you have several services that are customer facing or internet facing, if you will, that have a public IP address or a public DNS.
*   And they're available to anybody on the open internet.
*   And they might not even know what cloud is.
*   They might not even know what is it that you're sharing with them or where it's located, let's say.
*   And we see here-- I'm not seeing object storage just yet.
*   But let's see if we do.
*   And object storage is one of the services.
*   And let's assume that you have pictures on your object storage.
*   And, of course, the Autonomous Database or the Autonomous Transaction Processing Database Analytics, Oracle Analytics Cloud, the Autonomous Data Warehouse, Data Flow, Database Migration, GoldenGate, these are all services that sits on the Oracle Services Network.
*   And object storage is one of them.

### **2. A Practical Example: Object Storage**

*   And I was mentioning that you can have files in them, in that object storage, that bucket.
*   And on that bucket, you can make a pre-authenticated service request available, let's say, to a music file of something that is very unique to you.
*   It's not public domain.
*   Maybe you recorded this audio yourself.
*   And you make it available to someone else outside of OCI.
*   They might not even know what Oracle Cloud Infrastructure is or what cloud infrastructure as a service is or software as a service.
*   All they know is that they are downloading a music file.
*   And this bucket resides on the Oracle Services Network.

### **3. Scope and Availability of Services**

*   As you can see, we have over 100 services on the Oracle Services Network.
*   And so it's a wide selection, a flexible and powerful services that span infrastructure as a service, platform as a service, software as a service.
*   So let's say X as a service.
*   And they're hosted in the Oracle Services Network, which is a conceptual network from Oracle Cloud Infrastructure.
*   However, not all services are available on all regions.
*   So you might have one region with one set of services and another region with another set of services.
*   So that's very important as we'll see when we get to explaining the Oracle Services Gateway and maybe when we're doing the demo.
*   So Oracle services are accessible via IP addresses or fully qualified domain names, the DNS name that you assign or the service, in particular, assigns to that service that you're using.

### **4. Connectivity Options to the Oracle Services Network**

**Option 1: FastConnect**

*   So the connectivity options that you have to the Oracle Services Network, you can use FastConnect Public Peering.
*   You can use FastConnect Private Peering through the Services Gateway.
*   FastConnect Public Peering if you're going from on premises directly into the Oracle Services Network and you want to bypass the internet from on premises.

**Option 2: VCN Gateways (Sub-optimal)**

*   Obviously, your resources and your VCN can use the internet gateway to go ahead and retrieve them.
*   You can use the NAT gateway to go ahead and retrieve them.
*   That's not optimal because you're leaving OCI, your tenancy, to go out to the open internet and come back into OCI, into the Oracle Services Network.
*   Once you retrieve the service, then you go back to the open internet and come back into OCI, which is your tenancy.

**Option 3: The Services Gateway (Optimal)**

*   So it's better to either use FastConnect Public Peering or use the Oracle Services Gateway.
*   Now you can use private peering as well, but you need the Oracle Services Gateway, which allows the traffic to remain within Oracle Cloud Infrastructure.

**Option 4: Private Endpoints**

*   Then we also have another concept called the private endpoints.
*   That's basically when you assign a private IP address from your pool of private IP addresses that you have on your subnet to a service.
*   So it's an endpoint that is virtually connecting to the Oracle Services Network.
*   Let's say the Autonomous Transaction Processing, ATP.
*   Let's say that you assign a private endpoint.
*   It will make that Autonomous Transaction Processing database appear as a node in your subnet.

### **Summary of Connectivity Methods**

*   So that's how you can access the Oracle Services Network from on premises via FastConnect Public Peering or via FastConnect Private Peering VPN as well, but leveraging the Services Gateway.
*   You can also access the Oracle Services Network from within your VCN through the NAT gateway or the internet gateway.
*   We mentioned that that's not optimal, but it's possible or through the services gateway that bypasses the internet or through a private endpoint.

### **Conclusion**

*   So this covers pretty much the services the Oracle Services Network or OSN.
*   Thank you very much.
