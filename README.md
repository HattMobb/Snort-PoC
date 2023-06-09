
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


