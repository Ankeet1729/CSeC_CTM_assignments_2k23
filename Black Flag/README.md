# Black Flag





## Solution

so we were provided a `pcap` file in this challenge named `comm.pcap`. Now with this, I straight away opened `wireshark` and analysed the packets. I observed that there were only a few TCP packets in it. So I followed the TCP stream and in it I found that the starting few lines go something like this

```
......JFIF.....,.,......Exif..II*...........................b...........j...(...........1...
...r...2...........i...............,.......,.......GIMP 2.10.30..2023:05:02 02:13:37...................
```

now with this I knew that there was `JFIF file` in the pcap file. And my guess was that the flag would be written in that file.

So i used `binwalk` to extract the JFIF file

```
binwalk --dd='.*' comm.pcap
```

This gave me the extracted files and in one of the pictures I found my flag

##

## Flag

CSeC{if_you_had_fought_like_a_man_you_need_not_have_been_hang'd_like_a_dog}