# Cluster Copy 2

`ccp2` is a high-performance tool for efficiently copying data to cluster servers, designed for optimal speed and reliability. This version is written in Rust.


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

## Protocol ccp

| Offset Octet | bytes     | 
|--------------|-----------|
| 0            |  headcmd  |
| 1            |  length   |
| 2            |  length   |
| 3 ...65535   |  headdata |

#### headcmd
001  -> Auth <br>
002  <- - - - - - - - - - Auth ok <br>
011 next hosts *<br>
018 <- - - - - - - - - - hosts ok <br>
021 Connect *<br>
022 <- - - - - - - - - - all connect ok <br>
031 check program <br>
032 <- - - - - - - - - - no program <br>
033 Send program *<br>
034 <- - - - - - - - - - has program <br>
035 Run program <br>
036 <- - - - - - - - - - error runing program <br>
038 <- - - - - - - - - - all program runing <br>
041 file name *<br>
042 <- - - - - - - - - - erro crating file <br>
048 <- - - - - - - - - - file created <br>
051 type transfer data *<br>
052  <- - - - - - - - - - type transfer data ok <br>
058 data to copy *<br>
059 <- - - - - - - - - - numbre bytes copied <br>
061 check data *<br>
063 Disconect <br>

***\*headdata***

## Authors

- [@Franklin Diaz](mailto:fdiaz@adaptiveomputing.com)

