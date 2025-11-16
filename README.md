# Enterprise Multi-Building Network Topology (Draw.io)

This repository contains a custom-designed enterprise network topology created to practice professional network diagramming, logical segmentation, and multi-building infrastructure planning. The diagram models a realistic organizational layout with separate buildings, departments, servers, and structured LAN/WAN connectivity.

## Project Overview

The objective of this project was to design a clean, readable network architecture that demonstrates how real organizations separate users, services, and infrastructure across multiple physical locations. The topology includes two buildings, multiple departments, centralized server rooms, and proper distribution of network equipment.

The diagram incorporates:
- Two independent buildings (Headquarters and R&D)
- Four departments (Finance, HR, Software Engineering, Cybersecurity Operations)
- A dedicated server room in each building
- WAN edge routers and an inter-building internet link
- Distribution and access switches
- User endpoints connected through structured access layers

## Design Choices (Brief Report)

Several deliberate design decisions were made to keep the topology realistic and professionally structured:

### **1. Physical Separation of Buildings**
Each building is enclosed in its own container to clearly represent physical and logical separation. This mirrors how organizations often isolate local network infrastructure between sites.

### **2. WAN Edge Routing Above the LAN**
Routers were placed above the buildings and connected through a simulated ISP link.  
This reflects real-world architecture where:
- Routers manage WAN and site-to-site communication  
- Switches handle internal LAN distribution  
- WAN and LAN layers remain visually and functionally distinct  

### **3. Distribution and Access Layer Hierarchy**
Each building uses:
- One **distribution switch** to aggregate traffic  
- Separate **access switches** for each department  
This aligns with the common two-tier enterprise switching model and ensures a clean, scalable structure.

### **4. Departmental Segmentation**
Departments are grouped into their own logical containers, each with dedicated access switches and endpoints.  
This improves clarity and reflects how organizations segment teams, devices, and access policies.

### **5. Dedicated Server Rooms**
Both buildings include a server room.  
Roles include:
- File and database servers (Headquarters)  
- Code repository and CI/CD automation servers (R&D)  
Centralizing servers in each building replicates how equipment is physically organized for maintenance, cooling, and security.

### **6. Clear and Consistent Traffic Flow**
All switch-to-endpoint and router-to-switch links use directional arrows to illustrate intended data paths.  
This improves readability and provides a realistic representation of network flow within and between buildings.  

## License
This project is provided for educational and personal lab-building purposes.
