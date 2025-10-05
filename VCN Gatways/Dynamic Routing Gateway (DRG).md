### **Introduction to the Dynamic Routing Gateway (DRG)**

*   Hello.
*   And welcome to a brand new lesson.
*   This one on the Dynamic Routing Gateway.
*   My name is Sergio Castro with Oracle University.
*   And the DRG is my favorite product in OCI.
*   So let's go ahead and take a look and see the details of the dynamic routing gateway and the aspects of it.

### **1. What is the Dynamic Routing Gateway (DRG)?**

*   So the dynamic routing gateway is a virtual router.
*   This will allow you to connect beyond the internet to on-premises, to another cloud service provider, to a software-defined wide area network, basically anything that is outside of the open internet.
*   Now you can use it to establish FastConnect, that's a digital circuit, or IPsec connectivity to all of the above.
*   FastConnect to on-premises.
*   IPsec to on-premises.
*   Or FastConnect to another cloud service provider.
*   IPsec to another cloud service provider.
*   So all of the above basically.

### **2. Key Characteristics: Standalone Product**

*   And now the DRG is a standalone product.
*   So what does this mean?
*   Basically, it lives beyond the life cycle of a Virtual Cloud Network because it does not belong to the VCN.
*   Remember, that all the other gateways that we already covered, the internet gateway, the services gateway, the local peering gateway, the NAT gateway-- they all are within the Virtual Cloud Network.
*   So if you delete the VCN, all of those gateways go with the VCN.
*   They are deleted, but not the DRG.
*   If you want the VCN to leverage the DRG, then you need to attach it to a dynamic routing gateway.
*   And you can detach it later on and attach it to another VCN.
*   So it is a very powerful product.
*   And it's very different.
*   That's key.
*   It's very different from the other gateways that we have on a VCN.
*   Now after you attach a DRG to a VCN, you need to add route rules that will take you to that DRG, same as you do with other gateways.
*   That part is similar to it.

### **3. Border Gateway Protocol (BGP) and Route Advertisement**

*   Now regarding BGP, the Border Gateway Protocol.
*   Whenever you add a VCN, if you have an attachment like an IPsec connection or FastConnect that will take you to on-premises, then all CIDR blocks of that VCN subnets of the subnets of that VCN will be advertised to on-premises network.
*   And likewise, when you have that connectivity, all the route rules or all the route outsiders from the resources that you have on the on-premises side are going to be advertised to the DRG through BGP.

### **4. Use Cases and Scenarios for the DRG**

*   Now let's go ahead and take a look at several scenarios.
*   Basically, you leverage the DRG for creating global networks.
*   What does this mean?
*   You can connect to another cloud service provider.
*   You can connect to a software-defined wide area network.
*   And you can connect and scale your networks by connecting to other regions within OCI, be on your own tenancy or on someone else's tenancy.
*   You can do that and create a global network through remote peering connection, through FastConnect, IPsec, and leverage all of these resources to have a very robust, redundant, and scalable network.

### **5. Main Features of the DRG**

*   Now let's go ahead and take a look at the main features of the dynamic routing gateway, one of which is remote peering connection.
*   As we just saw, you can connect a DRG on one given region to another DRG that sits on another region.
*   And that other DRG might be in your same tenancy or in a third tenancy.
*   Someone else's tenancy or a tenancy that you have for different purposes on your organization.
*   And every single resource is an attachment to the DRG.
*   We mentioned that the VCN is an attachment to the DRG.
*   But also, the IPsec connection, also the remote peering connection, also the digital circuit FastConnect, and even inter-tenancy attachments as well.
*   Every single resource is an attachment to the dynamic routing gateway, that's why the DRG is a standalone product.
*   Now you can assign a different route table and policy to each network resource that is attached to your DRG.
*   Now regarding the ECMP, the Equal Cost Multipath routing.
*   If you enable this, then you're going to have an active-active configuration.
*   This is a feature that comes with the enhanced dynamic routing gateway.
*   If you don't enable ECMP, for example, on an IPsec connection, then you are going to be having an active standby.
*   So one tunnel is going to be carrying out the traffic and the other one is going to be in standby mode in case the first tunnel goes down.
*   If you enable ECMP, then both tunnels are active and both tunnels carry traffic.
*   So very important case.

### **6. Specific Use Cases Explained**

**Simplified Configuration:**

*   Now some use cases for the dynamic routing gateway-- basically, for simplified configuration.
*   So how is it solved?
*   It's a very powerful connection.
*   So typically, if you want to connect two VCNs, normally, you will use the local peering gateway.
*   And for that, you need to establish the local peering connection at the local peering gateway on the subnet, and then modify the route rules.
*   In this case, it's a very simple configuration.
*   If you attach two VCNs to a DRG-- and by the way, you can attach up to 300 VCNs to a DRG.
*   But if you attach two of them, then all you have to do is work with the route rules on the route tables, and point to the DRG as the next hop.
*   So, very simple configuration that you can start with leveraging your DRG.

**High Availability:**

*   Now high availability-- it's a use case for the DRG.
*   If you are going to be connecting to on-premises, then it is best practices to have two FastConnect connections going, let's say, from on-premises to a single OCI region.
*   But you can also establish high availability through a more complex configuration.
*   You might have two regions.
*   And you can have FastConnect going from OCI to one region, and then another FastConnect going to on-premises in the other region and leverage these two FastConnect connections.
*   In case one goes down, then you can use remote peering connection for transitive routing to reach the other region.
*   So you can work with high availability depending on your own configuration and on your own topology.

**Increased Scale and Complex Routing:**

*   And this will allow you to have increased scale.
*   And you can configure as you wish.
*   It's a very powerful resource.
*   And if you do that increase for scale, then you might have complex routing.
*   And with complex routing, that's because you can be very granular in your configuration, establish a very fine-grained control.
*   So you can go from simplified configuration to complex routing all using the same tool.
*   Again, it depends on your own configuration.

### **7. DRG Attachments and the Enhanced DRG**

**Attachment Types:**

*   Now we mentioned that we have several attachments.
*   And we already mentioned a couple of them.
*   This is a screenshot that we have from the Network Visualizer.
*   And as you can see, the dynamic routing gateway is represented at this circle right here.
*   And then everything is an attachment.
*   You see that we have several attachments, two VCNs through remote peering connections, one digital circuit.
*   So the attachment types that you have on the DRG are VCN attachments.
*   You have remote peering connection attachments, including DRGs that are in the same region.
*   You can establish a remote peering connection between two DRGs that are in the same region.
*   So it will replace basically the local peering gateway.
*   However, it's the local peering gateway is not going away.
*   It depends on your configuration.
*   One has advantages over the other.
*   And you can also have IPsec tunnel attachments, virtual circuit attachments.
*   And I mentioned before, you can also have inter-tenancy attachments.

**Legacy vs. Enhanced DRG:**

*   Now if you run into this screen that indicates an option for you to upgrade the DRG, that's because you are on a legacy DRG.
*   Since we launched the enhanced DRG over a year ago, every single DRG that you've deployed on OCI, every single new DRG that you deploy on OCI is going to be an enhanced DRG.
*   However, if you do have legacy DRGs in your tenancy, then you will have this option here to upgrade the DRG.
*   And if you upgrade, you need to be very careful because there's no going back.
*   The enhanced DRG is much more powerful.
*   For example, the legacy DRG can only have one VCN attachment.
*   Compare that with the enhanced DRG where you can have up to 300 VCN attachments.
*   So the enhanced DRG is very powerful.
*   If you upgrade, again, there's no going back.
*   And you also need to be very careful because it might carry service interruption as well.
*   So again, if you run into this message, it's because you are on a legacy DRG.

### **8. Connectivity and Routing Details**

*   Now let's go ahead and see some aspects of the DRG.
*   Supports connectivity from on-premises to multiple regions with FastConnect or site-to-site VPN connection.
*   That means that you go from on-premise to OCI on a given region.
*   And through transitive routing, you can reach the other regions.
*   Every single region, it can be reached from one FastConnect connection.
*   Now for redundancy, Oracle recommends deploying multiple FastConnect circuits.
*   And FastConnect is the best practices.
*   If for some cost effective configurations, you can also deploy redundancy with site-to-site VPN as well.
*   Now DRG is the gateway that will allow you to connect to Azure, Microsoft Azure.
*   So we have multiple regions, 12 to be precise, that has already the connectivity provision for you.
*   The physical cables are there.
*   And all you have to do is go ahead and enable the virtual circuits.
*   And you will have connectivity to Azure.
*   If you want to connect to another cloud service provider other than Azure, then you need a telecom provider.
*   But in the case of Microsoft Azure on 12 regions, you go directly FastConnect to express route.
*   And once you establish connectivity to on-premises or to another cloud service provider or to a software-defined wide area network, then you are going to be able to see the routes that are being received and sent to you through BGP.

### **9. Transitive Routing and Limitations**

*   Now let's go ahead and take a look at the typical configuration.
*   Here, we have transitive routing.
*   And transitive routing because we're going from on-premises or from another cloud service provider into OCI.
*   So we have this DRG connecting through a digital circuit to two of them, one going to a cloud service provider and the other one going to on-premises.
*   And then, that same DRG has a separate remote peering connection to a distant region.
*   Now we were mentioning that you can establish connectivity from on-premises to multiple regions, because you can enable transitive routing that's modifying the route tables and the route distributions in your DRG or creating new ones.
*   And then FastConnect will reach these two VCNs and through transitive routing will connect to this other DRG and reach this remote VCN as well.
*   You can configure that through transitive routing.
*   And we do have a lab for that that we recommend that you go and follow along.
*   Now, we want to be very clear that if you come into OCI through FastConnect, then the construct will not allow you to go out through FastConnect again.
*   So if you come into OCI through FastConnect, then you can reach a remote peering connection, you can reach the Virtual Cloud Networks.
*   However, we're not a telecom provider, so a route to another FastConnect or to an IPsec connection will not be allowed.

### **10. The DRG Route Engine**

*   So let's go ahead and take a look at the route engine for the dynamic routing gateway.
*   Here, we have three Virtual Cloud Networks.
*   We have a remote peering connection, one digital circuit, FastConnect circuit, and two IPsec connections.
*   So traffic coming into the DRG from either one of these resources reach the DRG route engine.
*   And then it distributes the traffic appropriately.
*   So in this case, we have packets coming in from a VCN into the DRG, and packets coming in from an IPsec connection into the DRG.
*   So analyzing the ones coming from the VCN, once they reach the DRG, then the route tables that you have on your VCNs and on your resources-- in this case, the VCN will route the traffic either to another VCN, to an IPsec connection through your FastConnect, or to your remote peering connection.
*   The route tables will take care of that.
*   If it comes in through IPsec, then the DRG will route it to a VCN or to the remote peering connection.
*   Again, going into the DRG through IPsec will not go out through the DRG, another IPsec connection, or FastConnect connection.

### **Conclusion**

*   So this covers the introduction to the dynamic routing gateway.
*   Thank you very much for watching.
