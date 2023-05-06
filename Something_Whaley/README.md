# Something_Whaley

So after running the image I understood that I am now in some other system with a flag probably hidden within

Now I tried this

`find -name flag` thinking there might be some file named flag

I got this output `./home/flag` but there was nothing in it (even after ls -a)

then I tried to cd into the root directory

There I did `ls`... Nothing

Next I tried ls -a

got this

`.  ..  .bash_history  .bashrc  .profile  .viminfo`

Now with my previous experience in bandit overthewire, I thought I had seen .bashrc and .profile before and I also remember that they don't really have much to offer. But the .viminfo bugged me for some reason (I might be wrong maybe .viminfo also doesn't generally carry any meaning either but I explored this because I had never seen such a thing before)

So I tried to `cat` it... At first glance it was looking like some wilderness of text again but I suddenly caught this

**CSeC{4nd_n0w_y0u_d0n7}** [ Flag 1 ]

I didn't try grep CSeC because I was not expecting to find the flag there (not because I am noob :-) )

OK so now it raised my interest in this entire directory

so I tried to cat all files in here and grep CSeC

`cat * | grep CSeC`  this didn't work saying 

`cat: '*': No such file or directory`

So I thought maybe this is what happens when there are hidden files in a directory. Therefore I tried this...

`cat .* | grep CSeC`  and bam!!! The output...

```
cat: .: Is a directory
cat: ..: Is a directory
echo CSeC{qu1t3_4n_3y3_y0u_g07_7h3r3}
export CTM="CSeC{n0w_y0u_s33_m3}"
	CSeC{4nd_n0w_y0u_d0n7}:
|3,0,0,0,1,0,1683221841,"CSeC{4nd_n0w_y0u_d0n7}:"
```

So here are your flags

## Flags

Flag 1: **CSeC{qu1t3_4n_3y3_y0u_g07_7h3r3}**

Flag 2: **CSeC{n0w_y0u_s33_m3}**

Flag 3: **CSeC{4nd_n0w_y0u_d0n7}**



