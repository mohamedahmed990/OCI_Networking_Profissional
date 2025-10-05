### **Introduction to Local Peering Gateways (LPG)**

*   Local peering gateway. This is the next lesson. Welcome to Oracle University. My name's Sergio Castro. And I am your instructor for this lesson. So let's go ahead and get started.
*   The local peering gateway is utilized to communicate to virtual cloud networks that sit on the **same region**.

### **How Local Peering Works: A Visual Example**

*   **Scenario:** Two VCNs in the same region need to communicate.
    *   **VCN-1:** CIDR block `10.0.0.0/16`
    *   **VCN-2:** CIDR block `182.168.0.0/16`
*   **Required Components:**
    *   A **Local Peering Gateway (LPG)** must be created in **each VCN**.
    *   The two LPGs must establish a **local peering connection** between them.
    *   Each VCN's route table must have a rule directing traffic for the peer VCN's CIDR block to its own LPG.
        *   *Example:* In VCN-2, a route rule would send traffic for `10.0.0.0/16` (VCN-1) to Local Peering Gateway 2.
*   **Communication Method:** Resources communicate using **private IP addresses**, even if they are in public subnets.

### **Key Requirements and Restrictions**

*   **Non-Overlapping CIDR Blocks:** The VCNs that are being peered **must not have overlapping CIDR blocks**.
    *   This restriction applies even to unused CIDR blocks within the VCN.
    *   If there is any overlap, the local peering connection will fail to establish.
*   **Gateway Requirement:** You need a local peering gateway **on each VCN** involved in the connection.

### **Comparing Connectivity Options for VCNs in the Same Region**

You have multiple options for connecting VCNs within the same region:

*   **1. Local Peering Gateway (LPG):**
    *   **Purpose:** Specifically designed for intra-region VCN peering.
    *   **Latency:** Has **less overhead and lower latency**.
    *   **Best Practice:** The **recommended and most efficient** method for connecting VCNs in the same region.
    *   **Restriction:** **No overlapping CIDRs** are allowed.

*   **2. Dynamic Routing Gateway (DRG) with VCN Attachments:**
    *   **Method:** Attach both VCNs to the same Dynamic Routing Gateway.
    *   **CIDR Handling:** **Allows VCNs with overlapping CIDRs** to be attached.
        *   However, resources in overlapping ranges **cannot communicate** with each other.
        *   You can assign a second, non-overlapping CIDR to a VCN to enable communication for those resources.
    *   **Flexibility:** This method provides a workaround if CIDR blocks overlap.

*   **3. Remote Peering Connection (RPC):**
    *   **Primary Purpose:** Designed for connecting VCNs in **different regions**.
    *   **Intra-Region Use:** Can be used within the same region, but it is **not the ideal choice**.
    *   **Latency:** Has more overhead and higher latency compared to an LPG.

### **Cross-Tenancy Peering**

*   All these connectivity options (LPG, DRG, RPC) can be used to connect VCNs in **different tenancies**.
*   This requires special **Identity and Access Management (IAM) permissions** and proper credentials to be configured.

### **Conclusion**

*   So thank you for watching.
