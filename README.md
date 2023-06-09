
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




