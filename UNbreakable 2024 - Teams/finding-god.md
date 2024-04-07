# finding-god

#medium #betaflash #osint #osm 

>David-Andrei Popa (contact@popadavid.ro)

## Description

Find the name of a place of worship located in Italy, beside water and close to hospital,park and a railroad. We checked on OSM, and there is only one.

Flag format is CTF{sha256(Location Name)}.

EX: CTF{sha256("Parrocchia S. Teresa di Gesù Bambino")}

## Solution

In order to solve the challenge, we need to use the `osm-search` tool (https://osm-search.bellingcat.com/). Applying our filters `(100m radius)`, we find that a church named `Oratorio di Santa Maria Annunziata` near the Vatican City fulfills our requirements. Furthermore, we pass the church's name through SHA256 and that's our flag.