
### **Introduction to the Service Gateway**

*   The service gateway.
*   This is the lesson for today.
*   My name is Sergio Castro with Oracle University, and thank you for joining.
*   Let's go ahead and see what we have in this lesson.
*   So in this lesson, we're covering the service gateway.
*   And this go hand in hand with one of the previous lessons we saw, which is the services network, the Oracle Services Network.

### **1. Purpose and Function of the Service Gateway**

*   And basically, this gateway provides secure and private access to the-- from your Virtual Cloud Network all the way to the Oracle Services Network, bypassing the internet.
*   So it is a conceptual network that it's an Oracle Cloud Infrastructure and it is reserved for Oracle services like object storage, the Autonomous Transaction Processing, database, the Autonomous Data Warehouse, digital assistants.
*   We saw Golden Gate as well in previous lessons.
*   So those are services that are accessible from the open internet.
*   So this is a construct that we have of all the services, and we've seen this diagram, as you can see, we have the internet gateway, the NAT gateway, and we have the Oracle services gateway going to object storage located on the Oracle Service Network.

### **2. Key Feature: Transitive Routing**

*   Now, host on your on-premise networks can reach the Oracle Services Network.
*   So private access through all the resources that you have on your VCN can privately access the resources from the Oracle Services Network.
*   Now, there's a difference between the other gateways that we have, the Internet Gateway, the NAT Gateway.
*   Those two gateways do not allow transitive routing.
*   The services gateway does allow transitive routing.
*   So what does that mean?
*   That means that resources on your on-premises, let's say you have a virtual machine or you have a physical computer on your local area network on-premises and then you're communicating your on-premises to the virtual cloud network via the dynamic routing gateway, that dynamic routing gateway can forward traffic to the services network to the service gateway and the service gateway will provide access by passing the internet to that resource.
*   That's sitting on your on-premises network.

### **3. Public Access and Regional Scope**

*   So public access with FastConnect, public peering is available as well.
*   So that means that you're not even touching your instances or your tenancy is going directly into Oracle Services Network by passing other resources that you have in your tenancy.
*   So a service gateway is a regional construct.
*   And regional means that it will provide access to the Oracle Services Network that are available only in that same region.
*   Let's say that we are in the San Jose region and you want to access resources on the San Jose region Oracle Services Network, then you can leverage the service gateway.
*   If you want to access resources that are in the Singapore region from that service gateway on San Jose, that service gateway will not provide you resources to the Oracle Services Network, resources on the Singapore region.

### **4. How Transitive Routing Works: A Detailed Look**

*   So this is what I was talking about transitive routing.
*   Here, as you can see, we have the on-premises network and we're using VPN or FastConnect.
*   You see the customer premises equipment and you have your private instance.
*   So that private instance is communicating to the dynamic routing gateway is going-- let's say that is FastConnect.
*   And then you can see that the dynamic routing gateway has a route table associated with it that communicates to the Oracle Services Gateway.
*   And then the Oracle Services Gateway has a corresponding route table that when-- that will send traffic coming back to the DRG.
*   And that's the way you can use transitive routing.
*   Now, you have a third route table, which is the subnet route table.
*   That's for your resources located on the VCN.
*   And that is transitive routing supported by the services gateway.

### **5. Benefits and Routing Propagation**

*   And again, this is private peering.
*   This is FastConnect private peering.
*   If you were to connect using public peering, then it goes directly into the Oracle Services Network.
*   It provides better latency because it doesn't have the extra hub of the DRG service gateway combo.
*   So VCNs or on-premises resources can access this Oracle Services Network without the need of the NAT Gateway or the Internet Gateway using the Oracle backbone.
*   Now, it is important to highlight that the addresses of the Oracle Services Network are being propagated.
*   All the CIDR blocks are being propagated to your on-premises resources or to your on-premise network via the Border Gateway Protocol.
*   And we saw that DRG route table and the service gateway route tables are supported, and they're attached to those gateways themselves.
*   So the DRG routes-- the traffic out to the service gateway and the service gateway returns the traffic to the DRG.

### **Conclusion**

*   And this concludes this lesson.
*   Thank you very much for watching.
*   Bye.
