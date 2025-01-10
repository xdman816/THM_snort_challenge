# THM_snort_challenge
Snort Challenge - Live Attacks walk-through 

# Scenario
We are informed that there is a brute force attack happening to our network, and we are tasked with finding out the source, service and port of the attack. Then we must write an IPS rule and deploy it in Snort in IPS mode.

# Step 1: monitor the network traffic using snort
We first check the network traffic and save it to a log file using the -l flag 

![traffic_log ](https://github.com/user-attachments/assets/54abe633-d2e4-4d49-a45c-4edc06b2dd58)

# Step 2: examine suspicious packet
There are many packets that are being sent or received on port 22, which is the port for SSH: 

![sus_packet](https://github.com/user-attachments/assets/a4ccbb7f-6046-48c8-ab4c-cfe93b8a634c)

When we filter for port 22, we see plenty of attempts coming from different IP addresses 

![filter_port_22](https://github.com/user-attachments/assets/fd1e25dc-d064-4707-b2fb-99a0563705f2)
![filter_port_22_pt2](https://github.com/user-attachments/assets/7cefb702-f783-40b6-a2cf-2970e616ad7e)

# Step 3: write rule to drop packets coming in on port 22 
We open up the rules configuration file and write a new rule that drops packets that coming in on port 22 

![open_rules_config](https://github.com/user-attachments/assets/535453b8-41d1-4f5b-a65a-50aafe5fbc9f)
![ips_rule](https://github.com/user-attachments/assets/fe188220-ec27-4e4c-9705-3ea57e7fb8bb)

# Step 4: run snort in IPS mode and implement rule 
Once the rule is implemented and we run snort in IPS mode, we see the packets are now being blocked. The brute-force attack has been stopped.

![snort_IPS_mode ](https://github.com/user-attachments/assets/01f9ed36-22b3-4d8e-8041-dbc6815d4041)
