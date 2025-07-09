# **Cybersecurity Incident Report: DDoS Attack Analysis (NIST CSF)**

## **1\. Security Event Summary**

In this simulated activity, a multimedia company experienced a **Distributed Denial of Service (DDoS) attack** that severely compromised its internal network for approximately two hours. The attack manifested as an incoming flood of **ICMP (Internet Control Message Protocol) packets**, which overwhelmed network services, rendering them unresponsive. During the incident, normal internal network traffic was unable to access any network resources, leading to a complete disruption of services.

The attack originated from a malicious actor exploiting an **unconfigured firewall**, which allowed the high volume of ICMP pings to penetrate and overwhelm the network.

**Initial Response:** The incident management team quickly intervened by:

* Blocking all incoming ICMP packets at the network perimeter.  
* Taking all non-critical network services offline to conserve resources.  
* Restoring critical network services to minimize operational impact.

Attack Source: Malicious actor(s)  
Targeted Systems: Internal network infrastructure, network services, web servers, and potentially other network-dependent systems.  
Estimated Impact: Two hours of network downtime, significant operational disruption, and potential financial losses due to service unavailability.

## **2\. NIST CSF: Identify (Categorize, Govern, Assess)**

### **Type of Attack and Systems Affected:**

* **Type of Attack:** This was a **Distributed Denial of Service (DDoS) attack**, specifically an **ICMP Flood attack**. An ICMP flood is a type of Denial-of-Service attack in which the attacker attempts to overwhelm a targeted device with ICMP echo-request packets (pings), causing the target to become unreachable by legitimate traffic.  
* **Systems Affected:**  
  * **Internal Network Infrastructure:** Routers, switches, firewalls, and other networking devices were overwhelmed.  
  * **Network Services:** All services dependent on the internal network, including web design, graphic design, and social media marketing solutions, became unresponsive.  
  * **Web Servers/Application Servers:** Any servers hosting the company's or clients' web applications were likely impacted, as they couldn't receive legitimate requests.  
  * **End-User Devices:** Employees' ability to access internal resources was compromised.  
  * **Firewall:** The unconfigured firewall was a key vulnerability that facilitated the attack's success.

## **3\. NIST CSF: Protect (Implement Safeguards)**

To further secure the organization’s assets and prevent similar incidents, the following systems and procedures need immediate updates or changes:

### **Immediate Action Plan:**

* **Firewall Reconfiguration and Hardening:**  
  * **Action:** Implement **strict firewall rules** to prevent unauthorized traffic. This includes "deny-all" by default, with explicit "permit" rules for only necessary ports and protocols. The previously implemented rule to limit ICMP packet rates should be permanently integrated.  
  * **Reasoning:** The unconfigured firewall was the primary entry point for the DDoS attack. Proper configuration is the first line of defense.  
* **Network Access Control (NAC) Implementation:**  
  * **Action:** Implement NAC policies to strictly control which devices and users can connect to the internal network and what resources they can access.  
  * **Reasoning:** Limits the blast radius if an endpoint is compromised and ensures only authorized devices communicate on the network.  
* **Bandwidth Management and Throttling:**  
  * **Action:** Configure network devices (routers, firewalls) to implement QoS (Quality of Service) and traffic shaping, allowing critical services to receive priority even under high load, and throttling non-critical traffic during an attack.  
  * **Reasoning:** Helps maintain essential service availability during a partial denial-of-service event, or allows for controlled shutdown.  
* **Employee Training and Awareness:**  
  * **Action:** Conduct mandatory training sessions for all employees on recognizing phishing attempts, social engineering tactics, and the importance of reporting suspicious activity.  
  * **Reasoning:** While not directly related to the ICMP flood, a robust security posture requires a strong human firewall to prevent other common attack vectors.  
* **Regular Security Audits and Penetration Testing:**  
  * **Action:** Schedule regular external and internal penetration tests and security audits, especially focusing on network perimeter devices like firewalls.  
  * **Reasoning:** Proactively identifies vulnerabilities (like unconfigured firewalls) before malicious actors can exploit them.

## **4\. NIST CSF: Detect (Monitor, Anomalies)**

To continuously monitor and detect similar incidents in the future, the organization should implement and refine the following:

* **Enhanced Network Monitoring Software:**  
  * **Capability:** Deploy or enhance network monitoring tools to provide real-time visibility into traffic patterns, bandwidth utilization, and connection states.  
  * **Detection:** Configure baselines for normal network activity. Alerts should be triggered for sudden spikes in traffic, especially for specific protocols like ICMP, or unusual traffic sources/destinations. This includes the existing "network monitoring software to detect abnormal traffic patterns."  
* **Intrusion Detection/Prevention Systems (IDS/IPS):**  
  * **Capability:** Utilize an IDS/IPS system (as was implemented) to actively inspect network traffic for malicious patterns, known attack signatures (e.g., specific DDoS attack types), and anomalous behavior.  
  * **Detection:** Configure IDS/IPS rules to specifically filter out and block suspicious ICMP traffic based on characteristics like packet size, frequency, and source reputation, going beyond simple rate limiting.  
* **Security Information and Event Management (SIEM) System:**  
  * **Capability:** Implement a SIEM solution to centralize and correlate logs from firewalls, IDS/IPS, routers, servers, and applications.  
  * **Detection:** Use SIEM to identify complex attack patterns that might be missed by individual tools, such as coordinated ICMP floods from multiple sources, or anomalies in user account activity (e.g., failed logins, unusual access times). Automated alerts for high-severity events should be configured.  
* **NetFlow/sFlow Analysis:**  
  * **Capability:** Collect and analyze NetFlow or sFlow data from network devices to gain deeper insights into traffic flows, source/destination conversations, and protocol usage over time.  
  * **Detection:** Identifies long-term trends and subtle changes in network behavior that could indicate reconnaissance, command-and-control communication, or a nascent DDoS attempt.  
* **Threat Intelligence Integration:**  
  * **Capability:** Integrate threat intelligence feeds into firewalls, IDS/IPS, and SIEM to automatically block or flag traffic from known malicious IP addresses and ranges.  
  * **Detection:** Proactively detects and blocks attacks originating from IPs identified as involved in previous DDoS campaigns.

## **5\. NIST CSF: Respond (Contain, Eradicate, Recover, Communicate, Analyze)**

A robust response plan is crucial for containing, neutralizing, and analyzing future cybersecurity incidents.

### **Containment and Neutralization:**

* **Automated Blocking Rules:** Implement automated rules within firewalls and IDS/IPS to dynamically block source IP addresses exhibiting suspicious behavior (e.g., exceeding ICMP rate limits).  
* **Traffic Scrubbing Services:** Utilize a third-party DDoS mitigation service or cloud-based scrubbing centers to divert and clean malicious traffic before it reaches the internal network.  
* **Service Isolation:** Have predefined procedures to isolate affected network segments or take non-critical services offline rapidly to prevent attack spread and conserve resources for critical operations.  
* **Blackholing/Null Routing:** For severe, sustained attacks, be prepared to null route (blackhole) traffic destined for specific IPs or subnets that are being heavily targeted.  
* **Network Segmentation:** Improve network segmentation to limit the blast radius of any successful attack, preventing it from affecting the entire internal network.

### **Data/Information for Incident Analysis:**

* **Firewall Logs:** For blocked traffic, permitted traffic, and rule hits.  
* **IDS/IPS Alerts and Logs:** For detected intrusion attempts, attack signatures, and anomalous network behavior.  
* **Network Flow Data (NetFlow/sFlow):** To understand traffic patterns, sources, destinations, and volume during the incident.  
* **System Logs:** From affected servers and network devices to identify resource exhaustion, service failures, and unexpected reboots.  
* **Application Logs:** To determine the impact on specific services and identify any application-level anomalies.  
* **Packet Captures (PCAPs):** For deep-dive analysis of specific malicious packets or traffic flows.

### **Improving Organization's Recovery Process:**

* **Regular Data Backups:** Implement automated, verified, and off-site backups for all critical data and system configurations.  
* **Disaster Recovery Plan (DRP) Testing:** Conduct regular (e.g., quarterly) drills of the DRP to ensure all personnel know their roles and all systems can be restored efficiently.  
* **Redundant Systems and Services:** Invest in redundant hardware and failover mechanisms for critical network services and infrastructure to ensure business continuity during an outage.  
* **Warm/Hot Standby Environments:** For critical applications, maintain warm or hot standby environments that can be quickly activated to minimize downtime during a major incident.  
* **Post-Incident Review (Lessons Learned):** After every incident, conduct a thorough post-mortem analysis to identify root causes, evaluate response effectiveness, and implement corrective actions. This includes reviewing procedures, tools, and team performance.

## **6\. NIST CSF: Recover (Restore, Implement Improvements, Communicate)**

To recover effectively from incidents and strengthen resilience, the organization must focus on restoring operations and implementing lasting improvements.

### **Information Needed for Immediate Recovery:**

* **Current Network Configuration Backups:** Crucial for restoring firewall rules, router configurations, and server settings.  
* **Critical Service Dependencies Map:** Understanding which services rely on each other to prioritize restoration.  
* **Contact Information for Key Personnel:** Incident response team, IT, vendors, and management.  
* **Access Credentials:** Secure access to critical systems (e.g., out-of-band management).  
* **System and Data Backups:** Verified, accessible backups of all critical data and operating systems.  
* **Network Diagram and Asset Inventory:** Up-to-date documentation of the network topology and all connected devices.

### **Processes for Organization Recovery:**

* **Prioritized Service Restoration:**  
  * **Procedure:** A documented plan outlining the order in which network services and systems should be brought back online, starting with essential business functions.  
  * **Goal:** Minimize business impact by restoring critical operations first.  
* **Forensic Analysis & Eradication:**  
  * **Procedure:** Conduct thorough forensic analysis to ensure all remnants of the attack (e.g., malware, backdoors) are eradicated from compromised systems before restoration.  
  * **Goal:** Prevent re-infection and ensure a clean environment.  
* **Post-Incident Communication:**  
  * **Procedure:** Establish clear communication channels for internal stakeholders (employees, management) and external parties (customers, partners, regulators if necessary) regarding the incident's status and resolution.  
  * **Goal:** Maintain transparency and trust.  
* **Vulnerability Remediation:**  
  * **Procedure:** Implement all identified protective and detective measures (e.g., fixing the unconfigured firewall, deploying IDS/IPS, setting up new monitoring alerts) before fully restoring services.  
  * **Goal:** Prevent recurrence of similar incidents.  
* **System Health Checks and Validation:**  
  * **Procedure:** After restoration, conduct comprehensive health checks and functional tests to ensure all systems and services are operating normally and securely.  
  * **Goal:** Confirm full recovery and stability.  
* **Lessons Learned Review:**  
  * **Procedure:** As mentioned in the "Respond" section, a formal post-incident review is critical. This process gathers insights from all involved teams, identifies what went well, what could be improved, and updates incident response plans, policies, and technical controls accordingly.  
  * **Goal:** Continuous improvement of the organization's cybersecurity posture and resilience against future attacks.