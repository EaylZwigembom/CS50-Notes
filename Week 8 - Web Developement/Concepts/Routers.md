To route data from one place to another, we need to make __routing decisions__. That is, someone needs to program how data is transferred from point A to point B.

You can imagine how data could take multiple paths from point A and point B, such that when a router is congested, data can flow through another path. __Packets__ of data are transferred from one router to another, from one computer to another.

__TCP/IP__ are two protocols that allow computers to transfer data between them over the internet.

__IP__ or __internet protocol__ is a way by which computers can identify one another across the internet. Every computer has a unique address in the world. Addresses are in this form:

```
#.#.#.#
```

Numbers range from `0` to `255`. IP addresses are 32-bits, meaning that these addresses could accommodate over 4 billion addresses. Newer versions of IP addresses, implementing 128-bits, can accommodate far more computers!

 In the real world, servers do a lot of work for us.

- Packets are structured as follows:
  ```
    0                   1                   2                   3  
    0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 
    +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
    |Version|  IHL  |Type of Service|          Total Length         |
    +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
    |         Identification        |Flags|      Fragment Offset    |
    +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
    |  Time to Live |    Protocol   |         Header Checksum       |
    +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
    |                       Source Address                          |
    +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
    |                    Destination Address                        |
    +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
    |                    Options                    |    Padding    |
    +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
    ```

Packets are standardized. The source and destination are held within each packet.

__TCP__, or transmission control protocol, helps keep track of the sequence of packets being sent.

Further, TCP is used to distinguish web services from one another. For example, `80` is used to denote HTTP and `443` is used to denote HTTPS. These numbers are __port numbers__.

When information is sent from one location to another, a source IP address, a destination IP address, and a TCP port number are sent.

These protocols are also used to fragment large files into multiple parts or packets. For example, a large photo of a cat can be sent in multiple packets. When a packet is lost, TCP/IP can request missing packets again from the origin server.

TCP will acknowledge when all the data has been transmitted and received.