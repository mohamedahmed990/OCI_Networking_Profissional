### **Introduction to Workload Migration in OCI**

*   In this module, we're going to discuss how to migrate workloads to OCI for real-world use cases.
*   The objectives of this course are to talk about workload migration strategies, including data migration, IP migration, and DNS migration.

### **1. Data Migration Strategies**

**Overview of Methods:**

*   Starting with data migration, there are a number of ways we could migrate data to Oracle Cloud Infrastructure's object storage service.
*   This can be done via the internet.
*   This can be done via FastConnect circuit, whether it's private peering or public peering.
*   We will go over the service gateway, which uses a private peering FastConnect circuit versus public peering, and the Data Transfer Appliance.

**Method 1: Internet Transfer**

*   In our sample topology, we have our on-premise data center, an OCI region, and our Oracle SaaS region, which hosts object storage.
*   The initial way we can migrate data to object storage is simply using the internet over secure channels, such as the HTTPS protocol.

**Method 2: FastConnect Public Peering**

*   In addition, we could establish a FastConnect public peering circuit to Oracle Edge.
*   This will allow BGP to advertise all of Oracle's public CIDRs to your on-premise data center.
*   This private dedicated circuit will be used in lieu of the internet circuit when migrating data to object storage.

**Method 3: FastConnect Private Peering with Service Gateway**

*   We can also use FastConnect private peering to migrate data to object storage.
*   In this example, we would need to establish an adjacency between the customer data center and the dynamic routing gateway over a private dedicated, private peering FastConnect circuit.
*   The dynamic routing gateway within the OCI region will need to have a VCN route table associated with it, which has a next hop of the object storage referencing the service gateway.
*   The service gateway is a construct within the OCI that allows access to publicly available Oracle SaaS services across private channels, whether it's from the VCNS point of view or on-premise data center point of view.
*   The service gateway will also need a VCN route table to know how to route traffic back to on-premise CIDRs.

**Method 4: Data Transfer Appliance**

*   The last option is to use a data transfer appliance.
*   This can be useful if you want to migrate petabytes of data in a short period of time.
*   A data transfer appliance is sent to the customer's on-premise data center site.
*   Data is transferred to it and then is securely shipped over to Oracle, which is then imported into object storage.

### **2. IP Migration: Bring Your Own IP (BYOIP)**

*   The next topic is Bring Your Own IP or BYOIP.
*   Oracle allows you to assign company-owned public IP CIDRs to OCI.
*   This allows for solution continuity and hard-coded dependencies.
*   We support IP pool management, and this allows us to maintain IP reputation.

**How BYOIP Works:**

*   In our sample topology, we have a consumer accessing a customer-owned IP range via the internet.
*   The data center will respond to any traffic that's coming in from the internet using these public IP CIDRs.
*   The on-premise data center is also connected to an OCI region using either a FastConnect or a VPN connection.
*   Leveraging OCI's BYOIP service, we can delegate these publicly-owned IP addresses to Oracle, and Oracle can start advertising these towards the internet.
*   This will allow the consumer to now come in via the internet towards Oracle's Edge to access the Oracle services within a given Oracle region.

### **3. DNS Migration and Traffic Management**

*   The final topic we'll discuss is DNS.
*   The Oracle Cloud Infrastructure Domain Name System allows you to manage DNS zones that your company owns.
*   In addition, public DNS on Oracle Cloud can be optimized for geolocation, latency, or other types of considerations when servicing things across the internet.

**Phased Migration with Ratio-Based Load Balancing:**

*   One thing we can do is utilize ratio-based load balancing to migrate fractions of traffic to our new cloud-hosted resources to test and validate prior to releasing to the internet.
*   We can then gradually migrate more traffic when we feel confident our user experience is up to par.
*   In our sample topology, we are delegating our public zone to OCI DNS.
*   Our consumer queries our OCI DNS services before reaching a publicly-hosted app in the data center.
*   We can then start provisioning our publicly-hosted app in OCI.
*   Leveraging OCI ratio-based load balancing, we could redirect 90% of the traffic to our existing data center and 10% of the traffic to the public cloud in OCI.
*   Once we feel more confident that our application and user experience is performing as it should, we can start migrating 100% of this workload to Oracle Cloud Infrastructure.

### **Summary**

*   In summary, we described the various options we could use for workload migrations in OCI.
