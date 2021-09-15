- [Binary](#binary)
- [Hexadecimal](#hexadecimal)
- [IP Addressing (IPv4)](#ip-addressing-ipv4)
  - [Classless addressing (~1995 to present)](#classless-addressing-1995-to-present)
  - [Classful addressing (~1995 and prior)](#classful-addressing-1995-and-prior)
  - [Address Types](#address-types)
  - [Private and Public Address](#private-and-public-address)
  - [Classless Inter-Domain Routing Notation (CIDR)](#classless-inter-domain-routing-notation-cidr)
  - [Making a subnet calculator](#making-a-subnet-calculator)
  - [Subnetting a network into smaller networks](#subnetting-a-network-into-smaller-networks)
  - [Basic router/NAT operations](#basic-routernat-operations)
  - [Variable Length Subnet Masking (VLSM)](#variable-length-subnet-masking-vlsm)
    - [Setting up VLSM Problem](#setting-up-vlsm-problem)
- [find port using nestat command](#find-port-using-nestat-command)
- [resources](#resources)
# Binary
![netowrking-01-binary-formart.png](images/netowrking-01-binary-formart.png)

![netowrking-02-binary-formart.png](images/netowrking-02-binary-formart.png)

# Hexadecimal

| Binary        | Decimal           | Hexadecimal  |
| ------------- |:-------------:| -----:|
| 0000 0000          | 0             | 0         |
| 0000 0001          | 1             | 1         |
| 0000 0010          | 2             | 2         |
| 0000 0011          | 3             | 3         |
| 0000 0100          | 4             | 4         |
| 0000 0101          | 5             | 5         |
| 0000 0110          | 6             | 6         |
| 0000 0111          | 7             | 7         |
| 0000 1000          | 8             | 8         |
| 0000 1001          | 9             | 9         |
| 0000 1010          | 10             | A         |
| 0000 1011          | 11             | B         |
| 0000 1100          | 12             | C         |
| 0000 1101          | 13             | D         |
| 0000 1110          | 14             | E         |
| 0000 1111          | 15             | F         |
| 0001 0000          | 16             | 10         |
| 0001 0001         | 17             | 11         |
| 0001 0010         | 18             | 12         |

# IP Addressing (IPv4)

Sample IP: 203.0.113.10


| Network Portion        | Host Portion           | 
| ------------- |-------------|
| 203.0.113        |             10  |
| Like zip code                 | Like street and number                | 

Binary format is: 
11001011 00000000 01110001 00001010

Every 8 bits is called octet.

## Classless addressing (~1995 to present)

Subnet mask tells us which portion of IP address is network and which portion is host. **Subnet mask does not have to fall every 8 bits!**

![netowrking-03-network-mask.png](images/netowrking-03-network-mask.png)

## Classful addressing (~1995 and prior)

Here subnet mask does not exist!

![netowrking-04-classABCD.png](images/netowrking-04-classABCD.png)

![netowrking-05-classA.png](images/netowrking-05-classA.png)

![netowrking-06-classB.png](images/netowrking-06-classB.png)

![netowrking-07-classC.png](images/netowrking-07-classC.png)

![netowrking-08-classD.png](images/netowrking-08-classD.png)

## Address Types

* Network Address
  * Identifier for a group of devices
  * "Network prefix"
  * Network address has zeros on host address portion
  ![netowrking-09-netowrk-address.png](images/netowrking-09-netowrk-address.png)
* Broadcast address
  * Identifier for all devices on a network
  * Broadcast address has ones on host address portion
  ![netowrking-10-broadcast-address.png](images/netowrking-10-broadcast-address.png)
* Host Address
  * Identifies unique device on a network
  * Only this address can be assigned to a device (computer)
  * Everything expect all zeros or all ones in the host portion
  ![netowrking-11-host-address.png](images/netowrking-11-host-address.png)

**Devices that are in the same network can talk each other directly.**

Sample network address:
![netowrking-12-sample-network-address.png](images/netowrking-12-sample-network-address.png)

Sample host address:
![netowrking-13-sample-host-address.png](images/netowrking-13-sample-host-address.png)

## Private and Public Address

* Private IP address range (can be used in home network, work network)
  * 10.0.0.0 - 10.255.255.255
  * 172.16.0.0 - 172.31.255.255
  * 192.168.0.0 - 192.168.255.255

All other addresses are public.

## Classless Inter-Domain Routing Notation (CIDR)

It is length of network portion - amount of ones.

203.0.113.10/24 means that the mask is 255.255.255.0 because 24 ones:
1111111 11111111 11111111 00000000 gives 255.255.255.0.

## Making a subnet calculator

For available hosts we subtract 2 because all zeros and all ones are assigned to network address and broadcast address.

| Bits        | Available networks           | Available hosts  |
| ------------- |:-------------:| -----:|
| 0          | 1    (2 pow 0)         | -  (1-2)        |
| 1          | 2    (2 pow 1)         | -  (2-2)       |
| 2          | 4    (2 pow 2)         | 2 (4-2)         |
| 3          | 8    (2 pow 3)         | 6 (8-2)         |
| 4          | 16             | 14 (6-2)         |
| 5          | 32             | 30         |
| 6          | 64             | 62         |
| 7          | 128             | 126         |
| 8          | 256             | 254         |
| 9          | 512             | 510         |
| 10          | 1024             | 1022         |

## Subnetting a network into smaller networks

We have to connect 8 offices together. ISP provides address range: 203.0.113.0/24 so the start address (network) is 203.0.113.0 and end address (broadcast) is 203.0.113.255. Using this range we have to create 8 sub-networks.

![netowrking-14-subnetting.png](images/netowrking-14-subnetting.png)

## Basic router/NAT operations

10.0.0.0/24 divide into 2 networks.
**Router job is to separate IP networks.**

![netowrking-15-router.png](images/netowrking-15-router.png)

![nat-28.png](images/nat-28.png)

## Variable Length Subnet Masking (VLSM)

We have to configure such network having from ISP CIDR: 10.0.48.0/21.
![netowrking-16-many-networks.png](images/netowrking-16-many-networks.png)

From the diagram we see that we will need 13 networks:
8 (for hosts) + 4 (for 4 routers) + 1 (routers on the top) = 13. Because routers on the top are connected directly they are in the same network so there is no need for additional router.

From 10.0.48.0/21 we have 11 bits available:
![netowrking-17-many-networks.png](images/netowrking-17-many-networks.png)

From these 11 bits we need 4 bits to create 13 networks so in every network we will have only 7 bits for hosts so it means that in every network we can have maximum 126 hosts and this is not enough for this scenario - that`s why we have to use **VLSM**.

### Setting up VLSM Problem

![networking-18-300-hosts.png](images/networking-18-300-hosts.png)

![networking-19-200-hosts.png](images/networking-19-200-hosts.png)

![networking-20-200-hosts.png](images/networking-20-200-hosts.png)

![networking-20-150-hosts.png](images/networking-20-150-hosts.png)

![networking-22-125-hosts.png](images/networking-22-125-hosts.png)

![networking-23-100-hosts.png](images/networking-23-100-hosts.png)

![networking-24-75-hosts.png](images/networking-24-75-hosts.png)

![networking-25-25-hosts.png](images/networking-25-25-hosts.png)

![networking-25-2-hosts.png](images/networking-25-2-hosts.png)

![networking-25-2a-hosts.png](images/networking-25-2a-hosts.png)

Table with amount of bits needed to address required amount of hosts.

![networking-26-table.png](images/networking-26-table.png)

Final network assignment:

![networking-27-assignment.png](images/networking-27-assignment.png)

# find port using nestat command

```
D:\>netstat -ano -p tcp | findstr 33714
  TCP    192.168.254.101:33714  3.235.96.62:443        CLOSE_WAIT      4184
```
Next we can find process name using command:
```
PS D:\> tasklist /fi "pid eq 4"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
System                           4 Services                   0      4 688 K
```



# resources
https://app.pluralsight.com/library/courses/network-layer-addressing-subnetting/table-of-contents   
https://en.wikipedia.org/wiki/File:NAT_Concept-en.svg   
https://documentation.meraki.com/MX/NAT_and_Port_Forwarding/Troubleshooting_Port_Forwarding_and_NAT_Rules   
https://www.youtube.com/watch?v=QBqPzHEDzvo   
https://www.youtube.com/watch?v=ujXr0i5EoHE   
