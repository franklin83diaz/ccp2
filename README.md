## Explanation of Operation

The goal of this program is to serve as a tool for copying data to multiple nodes simultaneously, in a secure and fast manner.

#### Required technology:
* Full-duplex network connection.
* SSH

#### Advantages:
* It takes the same amount of time to copy to two nodes as it does to copy to hundreds of nodes.
* It provides better data integrity compared to other UDP-based solutions.
* It doesn't require multicast/broadcast, making it compatible with cloud providers (AWS, GCP) that restrict the use of multicast/broadcast.
* easy use