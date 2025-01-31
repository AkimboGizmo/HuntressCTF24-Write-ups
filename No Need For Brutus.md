# No Need For Brutus

![[1HeadNoNeed.png]]


We are given a string to decode for the message. Then we need to use MD5 to make it a hash. This will give us the contents of the flag. Lets take this over to cyberchef.
![[2CyberchefNoNeed.png]]



Upon looking at the string it seems to have letters moved around to misconstrue the real message. I try ROT-13 and ROT-47, but did not get correct results.
![[3Rot13.png]]

![[4ROT47.png]]


So I try "ROT13 Brute Force" recipe. I get a readable message that I can try as the flag. It needed an amount of 10 revelations of ROT13.

![[5Decoded.png]]

So now we will take the decoded string and use MD5 to make it a hash.  
![[6MD5Hash.png]]


Now we can  encapsulate it with the "Flag{}" format. 

flag{c945bb2173e7da5a292527bbbc825d3f} 