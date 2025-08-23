# FIREWALL 
What is a firewall? A firewall is an agent responsible for allowing or denying traffic based on rules. Coming to every system/agent, it can't decide the right/wrong traffic. 
Note: Here, the traffic refers to the request we are sending to the servers. 
The firewall always follows the rules and decides which traffic is to be allowed and denied. We can also add rules manually so it works the way we want. 
Example: Let's say we are using an application, and I don't want the telnet port to be open and exposed to attackers, so I add a rule to deny the port connection 

For this i am using ufw which is a firewall solution where we can filter the traffic. 
Note: Every web traffic is classified into two types, which are inbound and outbound traffic. The inbound traffic are which connections coming into our system, and where outbound traffic are the connections going out from our system. 

lets start ufw with  
>sudo ufw enable

this command activate firewall and enable system startup

To check if the ufw status we can use 
>sudo systemctl status ufw

sam1 pic

Now with this we can confirm the system is active and ready to procees.
In order to see the added rule list
>sudo ufw status numbered

Note: No rules will be added as this kali linux machine is set to default and none restrictions are added to the list.

sam2

Here in the above image, we see only the status, which indicates active, and no rules.As i dont want port 23 connection let me add deny the port traffic with the rule.

>sudo ufw deny 23/tcp

>sudo ufw status numbered //To check the rules we added

sam3

Now we successfully added the rule, let's test it

__Case 1: NMAP__
>nmap -p 23 192.168.xxx.xxx
sam4

__Case 1: Netcat__
>nc 192.168.xxx.xxx 23
sam5

In both cases, we see the telnet (23 port) is refusing connection.i.e when the request is made, it is sent through the firewall as we set the rule it acts accordingly by refusing such connections.

This is the basic solution. This solution closes the port for the attackers and __for me__. so that i can't use remote connection now SO IS THIS THE SOLUTION?? __NO__ 
Closing the port is not the solution in this case, we can limit the access by specifing ip address, in some cases subnets can also be trusted with this scenario 

>sudo ufw allow from 192.168.xxx.xxx to amy port 23 proto tcp

sam6

the above command just allows only 1 ip which is mine to connect to that port not the other way around.this is also an example to imbound traffic.

Now we successfully added the rule, let's test it

__Case 1: NMAP__
>nmap -p 23 192.168.xxx.xxx
sam4

__Case 1: Netcat__
>nc 192.168.xxx.xxx 23
sam5
