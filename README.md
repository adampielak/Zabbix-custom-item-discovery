# Zabbix Custom Item Discovery
Bash script for interpreting delimiter separated text file to JSON suitable for Zabbix

# My case
Once upon a time I faced a need to constantly check status of nearly 50 remote services using their IP and PORT and get notified if one them is down

# How to use
1. Create file with your data (if you have used other delimiter instead of " ", also don't forget to change it for IFS in script)
1. Set text file as INPUT
2. Set OUTPUT filename
3.  Add UserParameter to your zabbix_agentd.conf
```bash
UserParameter=discovery_item_name,/bin/cat /path/to/your/JSON
```
4. Create new "Discovery Rule" in host or template
5. Set your discovery_item_name as "Key"
6. Create "Item prototype" using key names of your JSON
###### For example:
    Name: {#HOSTNAME} status
    Key: net.tcp.port[{#IP},{#PORT}]
