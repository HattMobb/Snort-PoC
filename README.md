
## Challenge 1 - HTTP IDS

Rules for detecting TCP port 80 traffic (both in and out): 


![Screenshot 2023-06-09 100803](https://github.com/HattMobb/Snort-PoC/assets/134090089/f7e47f9f-de83-451e-846a-214cb61f39ea)

Output against the given .pcap file: 

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/9d69d9f0-b508-4c96-a747-b30db9133862)


![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/5f3b4f1f-28ba-408b-b70f-6ccf1d099e96)

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/c81de4d0-7bc8-49db-ab0c-85bd4740fd2a)

Used -n to find the relevant packet for the question and locate the IP 
![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/8f018ce0-6023-417e-8923-9ce894f10fa8)

The packet: 

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/64f5bb06-fff5-4013-9f55-2085212fbcf0)


## Challenge 2 - FTP

Rules to catch all FTP traffic: 

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/89a45cf5-f715-45d7-a1f0-fa4663533f21)

Finding the FTP service name:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/ddd18b39-f3dd-46de-8244-6c9b34a56f1d)

-dvr :  detailed output

-n 10 :  first 10 packets 

-A1 : returns the line and the next line of the searched word

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/a1b6c287-abb3-442c-895c-423ca48b4707)


![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/6ce34e0f-9c6d-4475-a6c9-d4ac32430b6a)

Failed FTP login attempts generate the pattern "530 User" so I wrote a rule to catch this on inbound traffic:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/260bde4c-4df3-4a14-9fc6-47b353a3cdcd)

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/fc0254c5-e943-45b7-8366-74ddf53c10d6)


Successful FTP logis generate the pattern "230 User" so I wrote a rule to catch this on inbound traffic:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/d9418afc-8d40-4b07-8d91-816cf52cb2fe)


![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/8c027144-dac9-47d0-9001-359121f7ea41)

Each FTP login attempt with a valid username and bad password prompts a default message with  pattern "331 Password".
Rule to catch:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/711e2ecb-9401-4ebd-935a-750db3c2b0b5)


![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/71c1161e-2fb8-41ab-933b-c54539effb29)

For this question I just had to include a provided username with an invalid password:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/e6c38896-fab0-4aa3-b7ea-fa64bd1071aa)

7 failed attempts!

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/872711e6-2338-4883-94d8-7fd3c7236de6)

## Challenge 4 - PNG

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/f459bbd3-923c-49e4-977c-c115730dc5a1)

The rule:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/659ab00a-68d8-4062-ab1b-f926f680011d)

Detailed file read:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/7e811e67-c8b4-43ca-8a7c-0ecddc3d19f1)


Softaware version:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/81fb783c-a472-4283-9f51-9a89431c6aaf)


![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/de6fc54b-620c-45d1-a053-c4feab5463f7)

The rule:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/6b9a605b-c548-4460-9c13-e7bfb23e9f42)



Embedded image format:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/7a16d0d5-e944-4148-9501-a235b8c24c66)


## Challenge 5 - Torrent/Metafile

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/a946ac45-d1c5-479b-b873-5c513e373e70)

Torrent metafiles have a common name extension (.torrent) so this just required me to pipe in the value into the rule: 

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/d246fc49-923a-4485-95d2-5127751a2123)

Here we can see futher info on the file including host: 

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/e43b00e8-99e6-4853-a412-7e5ba34619f4)

## Challenge 6 Rule Troubleshooting

Running the first rule file, I got the following error:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/ef1b44c8-d63f-4b75-a8fc-8ee18fc8ef0d)

This indicated that a space was missing - an easy fix.

File 2 generated the following error: 

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/78c684bb-4dab-4746-87ef-b2bcff9dbeb2)

Indeed, checking the file revealed a missing port number in the rule:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/30ebe6d3-4e1c-43b2-bc37-7691dfabcb0f)

File 3 showed: 

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/ee5c06d2-2ef2-4f80-bd31-8fbe09aeb38e)

Both rules shared a conflicting sid, generating the error:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/7f56728c-17c0-45d1-8553-eb6c4e942e26)

The problem with file 4 was incorrect character use AND duplicate sid values:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/e47c3506-c6f1-471f-a4e0-b9a8a7835ae1)

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/6c8f86ed-5017-4032-a24b-0107079807bf)

File 5 had incorrect trafic direction (on the second rule) and incorrect ':' placement on both second an third rules  :

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/af45a509-d038-4ec1-8d60-b337eb04f0fe)

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/aca68488-2cb9-4b39-8079-8fdcb4f7910a)

File 6 didn't generate any errors but had a logic flaw - 

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/879b82a9-a8e2-4250-8f67-f7d7bc2c5ce3)

The content parameter required 'GET' to be passed rather than the HEX value.

File 7 also produced no errors but upon opening the file, wasn't specifying a msg value:

![image](https://github.com/HattMobb/Snort-PoC/assets/134090089/cfae4b7a-92cc-4b89-ba2e-9a390f69dd87)

This challenge was made much easier by simply reading error messages/codes!









