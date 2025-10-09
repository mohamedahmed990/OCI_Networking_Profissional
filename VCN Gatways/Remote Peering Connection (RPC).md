

### **Introduction to Remote Peering Connection**

*   Hello, I'm Sergio Castro with Oracle University, and welcome to this lesson on remote peering connection.
*   Very interesting topic, so let's go ahead and get started.

### **1. Purpose and Basic Setup**

*   Basically, you need the remote peering connection when you have two VCNs that need to communicate.
*   And these VCNs are located on different regions.
*   And we use San Jose and Singapore in previous examples.
*   So let's use these regions again, so Region 1 San Jose, Region 2 Singapore.
*   And as you can see on the Singapore side, VCN-2 has the CIDR block as 192.168.0.0/16.
*   And San Jose Region 1 has the CIDR block as 10.0.0.0/16.
*   So if you want to communicate them, you need to create DRG attachments.
*   And these DRG attachments are both the VCN.
*   That's one attachment.
*   And then you have to attach a remote peering connection to the DRG.
*   Once you attach that remote peering connection, you need to establish the connection itself.
*   And you indicate that through the Oracle Cloud ID of the other regions' remote peering connection.
*   And we'll see that when we get to the demo of doing a remote peering connection.
*   And in this case, you also need to establish a route rule on the route table.
*   So those are all the components that you need.

### **2. Required Components and Communication**

*   So basically, when you want to communicate with a remote peering connection, you need to allocate all of these resources, the remote peering connection attachment, the route rule and the route table, and even the security list.
*   And they will be communicating using private IP addresses.
*   So the remote peering connection will act as the connection point for the remotely peered VCN.

### **3. CIDR Blocks: A Critical Best Practice**

*   Now the two VCNs in the peering relationship must not have an overlapping CIDR block.
*   This is a best practices because best practices recommendation unlike the local peering gateway, that is a real hard limitation on the remote peering connection.
*   It's not a hard limit established by the OCI contract of the remote peering connection.
*   However, you will not be able to communicate these VCNs if they overlap.
*   So it is a best practice not to have overlapping CIDRs.

### **4. Scope and Tenancy Flexibility**

*   So typically, the remote peering connection is for VCNs located in different regions.
*   However, with the DRG enhancements that we put into place a couple of years back, now you can have remote peering connections within the same region.
*   So two VCNs located in the same region as we saw when we saw local peering connections is another option for communicating two VCNs in the same region.
*   And the VCNs can be located in different tenancies.
*   This is a fact.
*   Remote peering connection also with the enhancements of the DRG now allows remote peering connections for two VCNs located in different tenancies.
*   You do need identity and access management specialized privileges on both tenancies for this to happen, OK?

### **Conclusion**

*   So this concludes the remote peering connection presentation.
*   Thank you for watching.
