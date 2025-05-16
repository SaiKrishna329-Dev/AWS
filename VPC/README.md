VPC :

A VPC is a virtual network that you create in the cloud. It allows you to have your own private section of the internet, just like having your own network within a larger network. Within this VPC, you can create and manage various resources, such as servers, databases, and storage.

A VPC is a virtual network that closely resembles a traditional network that you'd operate in your own data center. After you create a VPC, you can add subnets.

Subnet: 

A subnet is a range of IP addresses in your VPC. A subnet must reside in a single Availability Zone. After you add subnets, you can deploy AWS resources in your VPC.

IP Addressing:

You can assign IP addresses, both IPv4 and IPv6, to your VPCs and subnets. You can also bring your public IPv4 and IPv6 GUA addresses to AWS and allocate them to resources in your VPC, such as EC2 instances, NAT gateways, and Network Load Balancers.

Network Access Contriol List:

A Network Access Control List is a stateless firewall that controls inbound and outbound traffic at the subnet level. It operates at the IP address level and can allow or deny traffic based on rules that you define. NACLs provide an additional layer of network security for your VPC.

AWS NACLs are called stateless because each packet is evaluated independently, with no memory of past connections, requiring you to handle both inbound and outbound rules explicitly.



Security Groups:

A security group acts as a virtual firewall for instances (EC2 instances or other resources) within a VPC. It controls inbound and outbound traffic at the instance level. Security groups allow you to define rules that permit or restrict traffic based on protocols, ports, and IP addresses.  

If this were a stateful firewall (like a security group), you’d only need to allow inbound traffic — return traffic would automatically be allowed.


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

