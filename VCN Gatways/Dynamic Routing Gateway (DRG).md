### **Introduction to the Dynamic Routing Gateway (DRG)**

*   Hello and welcome to a brand new lesson on the Dynamic Routing Gateway (DRG).
*   My name is Sergio Castro with Oracle University.
*   The DRG is my favorite product in OCI.

### **What is a Dynamic Routing Gateway (DRG)?**

*   The DRG is a virtual router.
*   It allows you to connect beyond the open internet to:
    *   On-premises data centers.
    *   Another cloud service provider.
    *   A software-defined wide area network (SD-WAN).
*   You can use it to establish two types of connectivity:
    *   **FastConnect:** A digital circuit.
    *   **IPsec:** VPN connectivity.
*   These connections can be made to any of the destinations listed above (on-premises, other cloud providers, etc.).

### **Key Difference: DRG vs. Other Gateways**

*   The DRG is a standalone product.
*   It exists independently of a Virtual Cloud Network (VCN) lifecycle.
*   Other gateways (Internet Gateway, Service Gateway, NAT Gateway, Local Peering Gateway) belong to a VCN and are deleted if the VCN is deleted.
*   The DRG is not deleted with a VCN.
*   To use a DRG, you attach it to a VCN.
*   You can detach it from one VCN and attach it to another, making it a very powerful and flexible product.

### **Routing and BGP**

*   After attaching a DRG to a VCN, you must add route rules to direct traffic to the DRG, similar to other gateways.
*   Regarding Border Gateway Protocol (BGP):
    *   When a VCN is attached to a DRG with an IPsec or FastConnect connection, all the VCN's CIDR blocks are automatically advertised to the on-premises network.
    *   Likewise, the route information (route advertisements) from your on-premises resources are advertised to the DRG via BGP.

### **Use Cases and Scenarios for the DRG**

*   The DRG is leveraged for creating global networks by connecting to:
    *   Other cloud service providers.
    *   Software-defined wide area networks (SD-WAN).
    *   Other regions within OCI (in your own or another tenancy).
*   You can scale your networks using:
    *   Remote Peering Connection.
    *   FastConnect.
    *   IPsec.
*   This enables robust, redundant, and scalable networks.

### **Main Features of the DRG**

*   **Remote Peering Connection:** Connects a DRG in one region to a DRG in another region, which can be in your same tenancy or a different one.
*   **Attachments:** Every resource connected to a DRG is considered an "attachment." These include:
    *   VCNs.
    *   IPsec connections.
    *   Remote Peering Connections.
    *   FastConnect digital circuits.
    *   Inter-tenancy attachments.
*   **Granular Routing:** You can assign a different route table and policy to each network resource attached to your DRG.

### **Enhanced DRG: ECMP and High Availability**

*   **Equal Cost Multi-path Routing (ECMP):**
    *   This is a feature of the *enhanced* DRG.
    *   When enabled, it provides an active-active configuration (e.g., for an IPsec connection, both tunnels carry traffic).
    *   If ECMP is not enabled, you have an active-standby configuration (one tunnel carries traffic, the other is on standby).
*   **High Availability Use Cases:**
    *   Best practice for on-premises connectivity is to have two FastConnect connections to a single OCI region.
    *   You can also achieve high availability with a more complex configuration across two regions, using FastConnect and Remote Peering Connection for transitive routing if one connection fails.

### **Simplified Configuration and Complex Routing**

*   **Simplified Configuration:**
    *   Instead of using Local Peering Gateways to connect two VCNs, you can attach both VCNs to a single DRG.
    *   You can attach up to 300 VCNs to one DRG.
    *   Configuration simply involves setting route rules on the route tables to point to the DRG as the next hop.
*   **Increased Scale and Complex Routing:**
    *   The DRG allows for increased scale.
    *   It provides fine-grained control, enabling you to create configurations that range from simple to highly complex, depending on your needs.

### **DRG Attachments and Upgrade Information**

*   Attachment types for a DRG include:
    *   VCN attachments.
    *   Remote Peering Connection attachments (even within the same region, which can replace a Local Peering Gateway).
    *   IPsec tunnel attachments.
    *   Virtual circuit attachments (FastConnect).
    *   Inter-tenancy attachments.
*   **Legacy vs. Enhanced DRG:**
    *   All new DRGs deployed on OCI are *enhanced* DRGs.
    *   If you see an option to "upgrade the DRG," you are using a legacy DRG.
    *   **Important Upgrade Notes:**
        *   The upgrade is irreversible.
        *   It may cause a service interruption.
        *   The enhanced DRG is much more powerful (e.g., supports 300 VCN attachments vs. only 1 for the legacy DRG).

### **Connectivity and Redundancy**

*   The DRG supports connectivity from on-premises to multiple OCI regions via a single FastConnect or IPsec connection using transitive routing.
*   For redundancy, Oracle recommends deploying multiple FastConnect circuits.
*   For a more cost-effective redundancy solution, you can also use site-to-site VPN (IPsec).

### **Connecting to Other Clouds**

*   The DRG allows you to connect directly to Microsoft Azure via FastConnect (ExpressRoute) in 12 pre-provisioned regions.
*   To connect to other cloud service providers, you will need a telecom provider for the FastConnect circuit.

### **Transitive Routing and Limitations**

*   **Transitive Routing:**
    *   Allows traffic from on-premises or another cloud to route through an OCI DRG to reach a VCN in a remote region.
    *   This is configured by modifying route tables and route distributions on the DRG.
*   **Key Limitation:**
    *   If traffic enters OCI through a FastConnect connection, it **cannot** exit through another FastConnect connection or an IPsec connection.
    *   OCI is not a telecom provider; traffic entering via FastConnect can only be routed to VCNs or Remote Peering Connections within OCI.

### **The DRG Route Engine**

*   The DRG has a central route engine.
*   All traffic from attached resources (VCNs, RPCs, FastConnect, IPsec) enters this engine.
*   Based on the configured route tables, the DRG distributes traffic to the appropriate destination.
*   **Example:**
    *   Traffic from a VCN can be routed by the DRG to another VCN, an IPsec connection, a FastConnect circuit, or a Remote Peering Connection.
    *   Traffic coming in from an IPsec connection can be routed to a VCN or a Remote Peering Connection, but not out through another IPsec or FastConnect connection (as per the limitation above).

### **Conclusion**

*   This concludes the introduction to the Dynamic Routing Gateway.
*   Thank you very much for watching.
