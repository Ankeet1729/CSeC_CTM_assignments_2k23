# Custom Crypto

### Info from the code

1. `claw` is a number between 1 to 9999
2. `THREAT` is a string with length <= 30 and with length being a prime number
3. `jack_o_lantern` is a list of digits of the binary representation of `claw`
4.  length of `epitaph` before compression is len(THREAT) squared
7.  Max length of jack_o_lantern is 14 (corresponding to 9999)
8.  ```cat chocolate.txt | base64 -d  gives output CSe1_37wg420}Cm1r_4s7y4C18_m3g31s2C{g114s_g7CSeC837w4320}C{1r_3s7y42S8_m1731s70{g18rs_g3ySeC{_7w4s10}CSgr_37_y420e_m1rw1s7y}g18___g314eC{gmw4s_s}```  (This also clears it out that THREAT is actually the flag)
9.  this has a length of  `146`
10.  So, len(THREAT) has to be >= ceil(sqrt(146)) 
11.  Also there are 19 unique characters in the above output + 1 repeated character `'C'` in `"CSeC"`
12.  So, there are at least 20 characters in the flag
13.  Therefore length of flag is either 23 or 29
14.  Now the first three letters are what it should be in the flag `CSe` but `C{` is missing
15.  So binary representation of claw starts with 11100
16.  Further on seeing CSeC entirely (without following `}` or preceding `{`) in the cipher, I can say that the binary represenation has the substring `01110`in it or it ends with `01`


### Following extra deductions after update

1. The binary representation is exactly 13 digit long
2. also now I know that the length of flag is 29
   1. 13*29=377 so we need to consider only first 377 characters
   2. solving the equation 145/377=x/13 we get x=5
   3. similar calculation does not yield an integer in the other case
   4. also with this I could conclude that there are exactly 5 1's in the binary representation
3. So the binary has to end with 1 (referring to point 14 above)



- Now the possible keys
  - 1110010000001
  - 1110001000001
  - 1110000100001

Finally after traversing the cipher text with the 4 definite 1's positions that I already knew of, I found out the actual key which is

`1110001000001`


Now traversing over the cipher manually I found out the flag

## Flag

CSeC{g18_m1r_37w4s_g31s7y420}
