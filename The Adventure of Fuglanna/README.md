ched my interests to the URB BULK packets# The Adventure of Fuglanna


## Problem Statement

Fieser püppchen is plotting to hide the flag away from tylluan in a desperate attempt to stop him from becoming CSeC core team member... To that end püppchen has decided to double encrypt the flag. However, Iolair, resourceful as always, was able to intercept the traffic between püppchen's computer and the hardware on which this encryption was occuring when püppchen tried to encrypt it for a second time. püppchen, realizing fuglanna were closing in, decided to erase the keys and the flag that was encrypted... Alas, they could only get back the remaining code and the trace Iolair captured. Tylluan suspected that they could retreive the flag in cleartext. Can you help the fuglanna?


## Solution

What I understood from this problem statement is that the pcap file is going to give me the ciphertext which is doubly encrypted along with the key to decipher it from the code given. So I opened wireshark.

Now this was something I never encountered before. USB protocols?? Hell, I can't even follow streams. Nor is there anything showing up in conversations section.

Since, wireshark was not making much sense I tried

`strings data.pcapng`

Didn't work. It was just some numbers that made no sense to me.

Now, I tried to look up about the USB protocol and USBHUB. Found out that these packets are captured when there is some communication between a USB device and a machine. Now the code provided is arduino, and there is something happening with the USB port. This led me to thinking that the flag might have been encrypted sometime using the Arduino IDE and the data would remain in the pcap. (Just an assurance of a previous guess.)

Now I thought the arduino code might tell me where to look in the pcap file by giving some information of the ports used.

So, I am not really well versed with arduino, and instead of doing it the hard way, I simply put in the code in chatGPT to help me out with understanding the code. So it goes something like this.


```
This code is implementing a simple encryption algorithm that XORs each character of a pre-defined flag with a one-time

pad generated from a secret key and a random initialization vector (IV). The encryption process is performed twice to 

produce a "double-encrypted" version of the flag.

Here's a step-by-step breakdown of what the code is doing:

    1. The code reads the value of digital pin 8 and stores it in the variable "iv". This value is used as the initialization vector (IV) for the encryption process.
    2. The code defines an array "output" to store the encrypted flag characters.
    3. The code enters a loop that processes each character of the pre-defined flag, one at a time.
    4. For each character, the code XORs the character with the current value of the IV (stored in "iv").
    5. The resulting XORed value is then processed bit-by-bit using the "key" array to generate a new value "acc".
    6. The new value "acc" becomes the new IV for the next iteration of the loop.
    7. The final value of "acc" is stored in the "output" array.
    8. After all characters have been processed, the "output" array contains the double-encrypted version of the flag.
    The code then prints the encrypted flag to the serial console.
```

Okay, so a lot was clear about the entire code, now the biggest challenge for me was to figure out about the USB protocol thing in wireshark

So, with a thought that this problem might have been influenced from another problem already made (because Quack Say was), I searched this in youtube

`USB packet analysis in wireshark`

and I got hooked up into this video by John Hammond

`https://www.youtube.com/watch?v=0HXL4RGmExo`

looked something similar to this challenge, so I followed along

but I soon realized that this is not going to be cracked in exactly the same manner as the `leftover capture data` is quite different in this case. I found them with this command

`tshark -r data.pcapng -V | grep "Leftover Capture Data" | less`

Then tried this

`tshark -r data.pcapng -V | grep "Copy of Transfer Flags" | less`

but didn't work again

Now although this didn't work, I did get a huge heads up in how I might have to proceed in this problem

Did some research now and found out something interesting. The packets that I actually should be interested in should be of type `URB_INTERRUPT_in` as this is what would have been typed by the keyboard and probably would contain something useful to us

So I exported only these packets to another file and called it `keystrokes.pcapng`

Now I was supposed to get the actual keystrokes from this pcap. I found out a few ways online to do this but none of it actually provided me with the keystrokes. All I could effectively get was this.

```
0000

8000

0000

0800
```

This was the leftover capture data of the packets in keystrokes.pcapng. I was expecting to get the hex of the values typed through the keyboard and map it according to [this](https://www.usb.org/sites/default/files/documents/hut1_12v2.pdf) pdf in page 53.

But now I was in a fix. As this seemed to be all the lead I got into this problem but which seems to have turned null and void. Maybe something else was used to hide the keys and encrypted flag

Nevertheless, I switched my interests to the URB BULK packets

Did quite some research but nothing felt like making any progress. Couldn't find anything useful even after like about half an hour of surfing the net. 

So this is all I could get out of this problem. Though couldn't solve it completely but I did learn about a new thing about these USB packets and maybe will be using this later on in other challenges. So, maybe this is the point after which I gave up. :-(
