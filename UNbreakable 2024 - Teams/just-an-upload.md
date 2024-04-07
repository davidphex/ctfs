# just-an-upload

#easy #wireshark #forensics #binwalk #skyv3il 

>David-Andrei Popa (contact@popadavid.ro)

## Description

Our team captured this traffic. Can you find what's in there ?

## Solution

Using `binwalk`, we are able to extract the contents inside the provided `pcapng` file. Upon extracting them, we find the `flag.txt` file.