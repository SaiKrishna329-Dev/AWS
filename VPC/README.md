VPC :

A VPC is a virtual network that you create in the cloud. It allows you to have your own private section of the internet, just like having your own network within a larger network. Within this VPC, you can create and manage various resources, such as servers, databases, and storage.

A VPC is a virtual network that closely resembles a traditional network that you'd operate in your own data center. After you create a VPC, you can add subnets.

Subnet: 

A subnet is a range of IP addresses in your VPC. A subnet must reside in a single Availability Zone. After you add subnets, you can deploy AWS resources in your VPC.

10.0.0.0/24 means 24 bits are redserved for network and rest are for available IPs (256 IPs) -- {(32-24=8)- 2^8 = 256 IPs}
10.0.140.0/20 means 20 bits are reserved, 32-20=12 --> 2^12=4096 IPs available.  means IPs available from 10.0.140.0 to 10.0.159.255. 

Decimal IP:  10     .   0   .  144  .   0

Binary IP : 00001010.00000000.10010000.00000000

Bit Index:  [--- Network Bits (20) ---][-- Host Bits (12) --]

Network bits (fixed):        00001010 00000000 1001---- ----

                                10       0      144
Host bits (variable):                       ---- ----
                                            ^ These can change

Range of IPs:
| Octet | Range                                                     |
| ----- | --------------------------------------------------------- |
| 1st   | 10 (fixed)                                                |
| 2nd   | 0 (fixed)                                                 |
| 3rd   | 144 to 159 → 16 values (because 4 bits can vary: 2⁴ = 16) |
| 4th   | 0 to 255 → 256 values (because 8 bits can vary: 2⁸ = 256) |

Third Octet (Binary)      Decimal     Fourth Octet
-----------------------   ---------   --------------
10010000 (start)          144         0 – 255

10010001                  145         0 – 255

...
10011111 (end)            159         0 – 255


IP Addressing:

You can assign IP addresses, both IPv4 and IPv6, to your VPCs and subnets. You can also bring your public IPv4 and IPv6 GUA addresses to AWS and allocate them to resources in your VPC, such as EC2 instances, NAT gateways, and Network Load Balancers.

Network Access Contriol List:

A Network Access Control List is a stateless firewall that controls inbound and outbound traffic at the subnet level. It operates at the IP address level and can allow or deny traffic based on rules that you define. NACLs provide an additional layer of network security for your VPC.

AWS NACLs are called stateless because each packet is evaluated independently, with no memory of past connections, requiring you to handle both inbound and outbound rules explicitly.

 NACLs are an additional layer of security that operates at the subnet level. They act as stateless traffic filters for inbound and outbound traffic at the subnet boundary.

 Unlike Security Groups, NACLs are associated with subnets, and each subnet can have only one NACL. However, multiple subnets can share the same NACL.

 NACLs consist of a numbered list of rules (numbered in ascending order) that are evaluated in order from lowest to highest.

 Each rule in the NACL includes a rule number, protocol, rule action (allow or deny), source or destination IP address range, port range, and ICMP (Internet Control Message Protocol) type.

 NACL rules can be configured to allow or deny specific types of traffic based on the defined criteria.

 They are stateless, which means that if an inbound rule allows traffic, the corresponding outbound traffic must be explicitly allowed using a separate outbound rule.

 Changes made to NACL rules may take some time to propagate to all the resources using the associated subnet.

Security Groups:

A security group acts as a virtual firewall for instances (EC2 instances or other resources) within a VPC. It controls inbound and outbound traffic at the instance level. Security groups allow you to define rules that permit or restrict traffic based on protocols, ports, and IP addresses.  

If this were a stateful firewall (like a security group), you’d only need to allow inbound traffic — return traffic would automatically be allowed.

 Security Groups act as virtual firewalls for Amazon EC2 instances (virtual servers) at the instance level. They control inbound and outbound traffic by allowing or denying 
 specific protocols, ports, and IP addresses.

    Each EC2 instance can be associated with one or more security groups, and each security group consists of inbound and outbound rules.
    Inbound rules determine the traffic that is allowed to reach the EC2 instance, whereas outbound rules control the traffic leaving the instance.
    Security Groups can be configured using IP addresses, CIDR blocks, security group IDs, or DNS names to specify the source or destination of the traffic.
    They operate at the instance level and evaluate the rules before allowing traffic to reach the instance.
    Security Groups are stateful, meaning that if an inbound rule allows traffic, the corresponding outbound traffic is automatically allowed, and vice versa.
    Changes made to security group rules take effect immediately.

<img width="1049" alt="image" src="https://github.com/user-attachments/assets/e5cff7aa-2c4d-4816-b1f5-0ad4adfd0a6a" />




| Feature             | NACL                            | Security Group            |
| ------------------- | ------------------------------- | ------------------------- |
| **Stateful?**       | ❌ No (Stateless)                | ✅ Yes (Stateful)         |
| **Applies to**      | Subnets                         | Instances                 |
| **Direction rules** | Need to specify **both** in/out | Only **inbound** needed   |
| **Rule evaluation** | Evaluates all rules             | Implicit deny after rules |


Routing:

Use route tables to determine where network traffic from your subnet or gateway is directed.

Gateways and endpoints:

A gateway connects your VPC to another network. For example, use an internet gateway to connect your VPC to the internet. Use a VPC endpoint to connect to AWS services privately, without the use of an internet gateway or NAT device.

Peering Connections:

Use a VPC peering connection to route traffic between the resources in two VPCs.

Traffic Mirroring:

Copy network traffic from network interfaces and send it to security and monitoring appliances for deep packet inspection.

Transit Gateways:

Use a transit gateway, which acts as a central hub, to route traffic between your VPCs, VPN connections, and AWS Direct Connect connections.

VPC Flow Logs:

A flow log captures information about the IP traffic going to and from network interfaces in your VPC.

VPC Connections:

Connect your VPCs to your on-premises networks using AWS Virtual Private Network (AWS VPN).

https://docs.aws.amazon.com/images/vpc/latest/userguide/images/vpc-example-private-subnets.png

<img width="683" alt="image" src="https://github.com/user-attachments/assets/fc43dfcb-a7e3-4346-a48f-7ea02edc87b2" />

