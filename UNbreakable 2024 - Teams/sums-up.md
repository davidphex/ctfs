# sums-up

#easy #skyv3il #wireshark #network #forensics

>David-Andrei Popa (contact@popadavid.ro)

## Description

Our SOC analysts saw some strange DNS traffic. Wanted you to figure out what was **exfiltated** , can you **check** it and **sum it up** ?

## Solution

Upon inspecting the given `pcap` file, we check the layer 4 information (transport layer) of the` DNS packets`. After getting a hint from the description, we take the `checksum` of each packet and combine them into a string. Passing them through `CyberChef`, we convert each value from hex and we get the flag.
