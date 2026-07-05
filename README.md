  <h1>OpenNebula Cloud Infrastructure Deployment & Management</h1>

  <p>
    This project involved the secure architecting of a private cloud environment using OpenNebula on CentOS 7. 
    The design prioritized Zero Trust principles and data protection, implementing LDAP-based centralized Identity 
    and Access Management (IAM) for granular Role-Based Access Control (RBAC). Security was reinforced via OVS-integrated 
    network segmentation, strict firewall policies, and systematic log auditing for threat detection. This implementation 
    serves as a functional model for secure Infrastructure as a Service (IaaS), demonstrating an understanding of encryption, 
    integrity, and operational resilience.
  </p>

  <h2>Security Implementation</h2>

  <h3>1. Identity & Access Management (IAM)</h3>

  <h4>LDAP Integration</h4>
  <p>
    I centralized identity management by configuring OpenNebula to authenticate against an external LDAP server. 
    This shifts authentication away from local fragmented files and reduces the attack surface by enforcing uniform 
    password policies across the infrastructure.
  </p>

  <h4>Role-Based Access Control (RBAC) & Principle of Least Privilege</h4>
  <p>
    I implemented granular Role-Based Access Control (RBAC) by mapping specific LDAP groups to OpenNebula roles. 
    Users were assigned only the minimum permissions required for their functions (e.g., "Operator" vs "Administrator"), 
    ensuring that potential damage from a compromised account is strictly limited.
  </p>

  <h3>2. Network & Traffic Security</h3>

  <h4>Network Segmentation</h4>
  <p>
    I utilized Open vSwitch (OVS) to create isolated virtual networks for different workloads. By segmenting the environment, 
    I implemented a defense-in-depth strategy that prevents lateral movement, effectively isolating a potential breach to a single segment.
  </p>

  <h4>Hardening</h4>
  <p>
    I used firewalld to enforce stateful packet inspection at the hypervisor level. I restricted inbound and outbound traffic 
    to only the necessary service ports (e.g., allowing Secure Shell (SSH) and specific management ports while dropping all other unauthorized traffic).
  </p>

  <h3>3. Data Protection & Encryption</h3>

  <h4>Encryption in Transit</h4>
  <p>
    I secured the management plane by proxying Sunstone traffic through Nginx with Transport Layer Security (TLS)/Secure Sockets Layer (SSL), 
    ensuring that all administrative sessions and credential exchanges are encrypted in transit.
  </p>

  <h4>Logging & Auditing</h4>
  <p>
    I configured rsyslog to capture and forward system logs to a centralized location. By segregating logs (e.g., using specific facilities like local6), 
    I ensured they are structured and ready for ingestion into a Security Information and Event Management (SIEM) system for forensic accountability and proactive threat detection.
  </p>
