# Networking-Diagnostics-Firewall-Lab

## Overview
This lab simulates a real-world Tier-1 helpdesk scenario focused on diagnosing and resolving network connectivity issues. The client can connect to Wi-Fi but has no Internet access. Throughout the project, I perform end-to-end troubleshooting using tools like ping and tracert to trace network paths and isolate the point of failure. After identifying the issue through pfSense firewall analysis, I apply rule adjustment to restore Internet connectivity. This lab highlights my ability to analyze connectivity issues, work with firewalls, and apply targeted network fixes 

## Environment:
Windows VM → Client workstation
Ubuntu Server VM → Internal server
pfSense → Router/firewall
All devices share the same subnet.

## Scenario: 
*Recieved a ticket from a coworker.* 

<img width="1652" height="941" alt="image" src="https://github.com/user-attachments/assets/890bbc1b-53d2-487b-a569-2e714d4f677f" />


## Process & Screenshots

### 1. Testing external connection
 
  *I pinged google.com on the clients computer to test external connectivity and also pinged the IP address directly to verify that the issue was not related to DNS. Both tests failed confirming that the problem lies beyond name resolution.*  
  

<img width="1712" height="949" alt="image" src="https://github.com/user-attachments/assets/a11263e7-94c9-46b2-b2da-c64881f174a7" />


### 2. Test Local Connectivity

*I verified LAN communication by performing a ping test between devices on the same subnet, confirming proper Layer 2 and Layer 3 connectivity.* 

<img width="976" height="271" alt="image" src="https://github.com/user-attachments/assets/894778e5-ea1d-44e7-892d-049d3eeb4ecc" />

### 3. Ping the Router (Gateway)

*I pinged the router which failed. From this I concluded that the router is likely the source of the issue. To prove my hypothesis I ran a traceroute which confirmed that the local gateway is not responding.*

<img width="1023" height="432" alt="image" src="https://github.com/user-attachments/assets/3adca636-f5a0-406c-be79-4783a5b8457d" />

### 7. Inspect Firewall Rules in pfSense

*I logged into the pfSense GUI using its IP address and reviewed the firewall rules. I removed the rule explicitly denying all outbound traffic from the Windows server which successfully resolved the connectivity issue.*

<img width="1034" height="767" alt="image" src="https://github.com/user-attachments/assets/748be60d-fabc-4fce-a750-6842dcbac535" />

### 8. Technician Response

*I verified that your system was connected to the local network but unable to reach external websites due to a firewall rule on our router. I’ve updated the configuration to allow secure web traffic, and your Internet access should now be fully restored.*  

<img width="1714" height="993" alt="image" src="https://github.com/user-attachments/assets/228467d0-c29d-4cc4-9277-a87f04504fd3" />



### 9. Internal Notes
 
*Confirmed LAN reachability. External ping and traceroute failed beyond gateway. Verified firewall logs in pfSense showing blocked packets. Created new allow rule for outbound TCP ports 80/443. Verified successful Internet connectivity post-change.* 

<img width="1724" height="992" alt="image" src="https://github.com/user-attachments/assets/ccedddbc-e524-425d-a97b-e42a80dd4924" />


## Key Takeaways
- Practiced real-world network troubleshooting using ping and tracert.
- Identified and resolved firewall misconfiguration in pfSense.
- Reinforced logical, step-by-step diagnostics and escalation workflow.
- Documented issue lifecycle in osTicket to simulate professional helpdesk operations.

## Author
**Hamze Ashur**  
Cyber Defense & Analysis Student | Aspiring IT Support & Security Professional  
 [GitHub](https://github.com/hamzaashur22)

