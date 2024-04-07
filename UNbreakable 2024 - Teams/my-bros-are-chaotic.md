# my-bros-are-chaotic

#ganglang #medium #skyv3il #steganography #chaotic #esoteric

> David-Andrei Popa (contact@popadavid.ro)

## Description

My friends have a theory about some chaotic events which are going to happen. Please decipher their message for national security matters, as it seems to be in their unique gang dialect. Flag Format: ctf{...}
## Solution

While learning about `chaotic steganography`, we stumble upon this tool https://github.com/zvut/Two-Tier-Hybrid-Steganography-Approach-using-Chaos-Theory. Chaotic steganography uses image shuffling and randomness to encode secret messages.

Warning! You might be tempted to say that the provided picture is similar to a `Piet` image (https://esolangs.org/wiki/Piet), but it is different.

This is what an encoded image (low res) looks like:

![Encoded picture | center | 192](https://raw.githubusercontent.com/zvut/Two-Tier-Hybrid-Steganography-Approach-using-Chaos-Theory/master/crenc.png)


By using the tool, we are are to extract a sequence of instructions, specific to the `GangLang` [esoteric programming language](https://esolangs.org/wiki/GangLang). 

The sequence:

```
YO SMOKE my 9802
YO RAP my 
YO SMOKE my 13460
YO RAP my 
YO SMOKE my 10405
YO RAP my 
YO SMOKE my 15135
YO RAP my 
YO SMOKE my 11887
YO RAP my 
YO SMOKE my 14646
YO RAP my 
YO SMOKE my 9028
YO RAP my 
YO SMOKE my 9609
YO RAP my 
YO SMOKE my 12998
YO RAP my 
YO SMOKE my 2306
YO RAP my 
YO SMOKE my 13227
YO RAP my 
YO SMOKE my 9026
YO RAP my 
YO SMOKE my 11669
YO RAP my 
YO SMOKE my 2402
YO RAP my 
YO SMOKE my 11450
YO RAP my 
YO SMOKE my 2603
YO RAP my 
YO SMOKE my 9025
YO RAP my 
YO SMOKE my 10610
YO RAP my 
YO SMOKE my 2707
YO RAP my 
YO SMOKE my 12101
YO RAP my 
YO SMOKE my 10610
YO RAP my 
YO SMOKE my 9027
YO RAP my 
YO SMOKE my 11664
YO RAP my 
YO SMOKE my 2704
YO RAP my 
YO SMOKE my 12101
YO RAP my 
YO SMOKE my 10610
YO RAP my 
YO SMOKE my 2810
YO RAP my 
YO SMOKE my 9028
YO RAP my 
YO SMOKE my 9606
YO RAP my 
YO SMOKE my 12999
YO RAP my 
YO SMOKE my 13690
YO RAP my 
YO SMOKE my 10817
YO RAP my 
YO SMOKE my 10819
YO RAP my 
YO SMOKE my 10817
YO RAP my 
YO SMOKE my 10818
YO RAP my 
YO SMOKE my 15626
YO RAP my 
```

According to the [GangLang wiki](https://esolangs.org/wiki/GangLang), `YO SMOKE` sets a variable to the square root of the specified value and `YO RAP` prints the given variable.

In our case, we can use ChatGPT to quickly get the square root of each number, transform it into an integer, and then convert it to an ASCII character to get the flag.

```
To find the square root of each of these numbers and then convert them into integers and finally to ASCII characters:

1. √9802 ≈ 99.000 → Rounded to 99 → ASCII: "c"
2. √13460 ≈ 116.000 → Rounded to 116 → ASCII: "t"
3. √10405 ≈ 102.000 → Rounded to 102 → ASCII: "f"
4. √15135 ≈ 123.000 → Rounded to 123 → ASCII: "{"
5. √11887 ≈ 109.000 → Rounded to 109 → ASCII: "m"
6. √14646 ≈ 121.000 → Rounded to 121 → ASCII: "y"
7. √9028 ≈ 95.000 → Rounded to 95 → ASCII: "_"
8. √9609 ≈ 98.000 → Rounded to 98 → ASCII: "b"
9. √12998 ≈ 114.000 → Rounded to 114 → ASCII: "r"
10. √2306 ≈ 48.000 → Rounded to 48 → ASCII: "0"
11. √13227 ≈ 115.000 → Rounded to 115 → ASCII: "s"
12. √9026 ≈ 95.000 → Rounded to 95 → ASCII: "_"
13. √11669 ≈ 108.000 → Rounded to 108 → ASCII: "l"
14. √2402 ≈ 49.000 → Rounded to 49 → ASCII: "1"
15. √11450 ≈ 107.000 → Rounded to 107 → ASCII: "k"
16. √2603 ≈ 51.000 → Rounded to 51 → ASCII: "3"
17. √9025 ≈ 95.000 → Rounded to 95 → ASCII: "_"
18. √10610 ≈ 103.000 → Rounded to 103 → ASCII: "g"
19. √2707 ≈ 52.000 → Rounded to 52 → ASCII: "4"
20. √12101 ≈ 110.000 → Rounded to 110 → ASCII: "n"
21. √10610 ≈ 103.000 → Rounded to 103 → ASCII: "g"
22. √9027 ≈ 95.000 → Rounded to 95 → ASCII: "_"
23. √11664 ≈ 108.000 → Rounded to 108 → ASCII: "l"
24. √2704 ≈ 52.000 → Rounded to 52 → ASCII: "4"
25. √12101 ≈ 110.000 → Rounded to 110 → ASCII: "n"
26. √10610 ≈ 103.000 → Rounded to 103 → ASCII: "g"
27. √2810 ≈ 53.000 → Rounded to 53 → ASCII: "5"
28. √9028 ≈ 95.000 → Rounded to 95 → ASCII: "_"
29. √9606 ≈ 98.000 → Rounded to 98 → ASCII: "b"
30. √12999 ≈ 114.000 → Rounded to 114 → ASCII: "r"
31. √13690 ≈ 117.000 → Rounded to 117 → ASCII: "u"
32. √10817 ≈ 104.000 → Rounded to 104 → ASCII: "h"
33. √10819 ≈ 104.000 → Rounded to 104 → ASCII: "h"
34. √10817 ≈ 104.000 → Rounded to 104 → ASCII: "h"
35. √10818 ≈ 104.000 → Rounded to 104 → ASCII: "h"
36. √15626 ≈ 125.000 → Rounded to 125 → ASCII: "}"
```
