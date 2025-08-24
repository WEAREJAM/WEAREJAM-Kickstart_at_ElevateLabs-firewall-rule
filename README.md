# WEAREJAM-Kickstart_at_ElevateLabs-firewall-rule

## Firewall Rules with UFW

## What is a Firewall?
A firewall is an agent responsible for allowing or denying traffic based on rules. Every system on its own cannot decide what traffic is right or wrong, so firewalls enforce rules to manage this.  

**Note:** Here, traffic refers to the requests we send to servers.  

The firewall always follows the defined rules and decides which traffic is to be allowed or denied. We can also add rules manually to make it work the way we want.  

### Example
If we are using an application and do not want the Telnet port (23) to be exposed to attackers, we can add a rule to deny connections on that port.  

---

## UFW (Uncomplicated Firewall)
For this setup, we are using **UFW**, which is a firewall solution that filters traffic.  

**Traffic Types:**
- **Inbound Traffic:** Connections coming *into* our system.  
- **Outbound Traffic:** Connections going *out* from our system.  

---

## Starting UFW
To enable UFW:  
```bash
sudo ufw enable

## Example - HTTP port

