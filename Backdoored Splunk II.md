
# <span style="color:rgb(0, 0, 0)">Backdoored Splunk II</span>

![[1BackHeader.png]]

###### <span style="color:rgb(0, 0, 0)">Challenge Description:</span>
![[2ChallDescip.png]]

<span style="color:rgb(0, 0, 0)">I start by downloading the zip file and then unzipping it.</span>
![[3Download.png]]
![[4Unziped.png]]

<span style="color:rgb(0, 0, 0)">I then try visiting the website and port provided by the challenge. This returns an error for "Missing or invalid Authorization header".</span>
![[5VisitingWebSite.png]]

<span style="color:rgb(0, 0, 0)">I then try using the grep command and some keywords like "Authorization, header, flag, etc." Nothing of interest was found.</span>

<span style="color:rgb(0, 0, 0)">So I move into the directory and look at some of the PowerShell scripts for anything interesting.</span>
![[6Lookingthroughfiles 1.png]]
![[6_1powershell.png]]

<span style="color:rgb(0, 0, 0)">While looking through the scripts, I found the "dns-health.ps1" script that contained a "STRinG" of Char code.</span>
![[9charcode.png]]

<span style="color:rgb(0, 0, 0)">Taking the char code over to cyberchef, we can begin decoding it. After using "Comma" as the delimiter and a Base of 10, we get a decoded message. Within the decoded text there is a Base64 string. We can put that string back into cyberchef.</span>
![[10decodechar.png]]


<span style="color:rgb(0, 0, 0)">Lets now decode it using the From Base64 recipe. We have the decoded string. Now there is another base64 encoded string we can put back into cyberchef.</span>
![[11decodebase64.png]]

<span style="color:rgb(0, 0, 0)">Finally we receive a completely decoded message. This seems to be the backdoor we were looking for.</span>
![[12decode2ndbase64.png]]


<span style="color:rgb(0, 0, 0)">We can now use PowerShell to store the hash-able header.</span> 
![[13Hashable.png]]

<span style="color:rgb(0, 0, 0)">Then we can invoke the web request and receive a 200 OK response. The response content contains yet another base64 encoded string. Lets go back to cyberchef one last time to decode it.</span>
![[14contentreturn.png]]


D<span style="color:rgb(0, 0, 0)">ecoding the base64 sting now returns the "flag" in plain text.</span>
![[15decodeFLAGbase64.png]]

<span style="color:rgb(0, 0, 0)">flag{e15a6c0168ee4de7318f502439014032}</span> 