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
# resources
https://app.pluralsight.com/library/courses/network-layer-addressing-subnetting/table-of-contents