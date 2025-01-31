# Red Phish Blue Phish Challenge


![[1HeadRedBlue.png]]

Reading the instructions and hints of the challenge, we can see that this will be an SMTP server we are working with. We are given the netcat command to utilize when we start the machine. This will connect us to the the SMTP server.
![[2Startingmachine.png]]

We receive the syntax "nc challenge.ctf.games 31297" for this instance created. The challenge also mentions "Remember your OSINT ;)" So we should use OSINT techniques to research the company the phishing attempt is targeting. Searching the name given of the target company and employee we find a web page for the target.
![[3OSINT.png]]
Note: seems that the person that would be most trusted for anything related to IT within the company would be, Joe Daveren.

We will attempt to use the given info and the OSINT obtained info in order to send a phishing email. Using the EHLO command we get a reach back from the server.
![[4EhloF.png]]


Typing the command HELP gives us what commands are accepted in this server.
![[5HELP.png]]


Now we will use the IT security managers name and use the same format of the username that is susceptible to phishing, we can start to construct our email. Using the command "MAIL TO:"
![[6MAILTO.png]]

We can now us the "RCPT TO" command to add the recipient. 
![[7RCPT.png]]

Finishing up with the subject and body of the email. Using the given username susceptible to phishing and the given Netcat syntax, we are unable to send the SMTP mail due to the shell capability. The mail should send using a "." one a separate line at the bottom of the mail to be sent. This should exit the mail editing format of the DATA section and send the mail to the recipient.
![[8CompleteF 1.png]]
NOTE: Unfortunately this does not work as intended due to the weak shell.

Upon further research I am informed that you can use the "-C" tack in the Netcat command. This triggers the "." and return as the way of completing the mail data entry. So repeating the same steps but using "-C" we are able to send the mail and get a return with the flag.
![[9CompleteCorrect.png]]

flag{54c6ec05ca19565754351b7fcf9c03b2}




