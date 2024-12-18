# Here is my MISC Solution
- [Welcome](#challenge1)
- [Asteroid](#challenge2)
- [SPACE ADVENTURE](#challenge3)
- [Cotisation](#challenge4)
- [Discord1](#challenge5)
- [Discord2](#challenge6)

---
## Challenge1
Name : `Welcome` <br />
Points :10 <br />
Description : <br />

>Welcome to the Securinets ISITCOM CTF Bootcamp!<br />
>This is your first step into the exciting world of Capture The Flag (CTF) challenges! The goal is to solve as many challenges as possible to prepare for the main Securinets ISITCOM CTF event. Each challenge requires a "flag" to be validated. A flag is a secret
><br />
>string that starts with "SECURINETSISITCOM{" and ends with "}".<br />
>To get you started, here's a free flag: SECURINETSISITCOM{bootcamp_welcome_flag}. Enter it in the edit box below to validate this challenge and begin your journey.<br />
>Good luck, and see you at the main event!<br />

Solution : 	<br />
`SECURINETSISITCOM{bootcamp_welcome_flag}`



## Challenge2
Name : `Asteroid` <br />
Points :150 <br />
Description : 
>STOPPP the Asteroid PLSSS!! From here :  `nc 151.80.133.55 8888` <br />

Solution : 	<br />
We got an Asteroid that going to hit the earth in this challenge and our mission is to protect the earth<br />
![image](https://github.com/user-attachments/assets/8e4e3327-8f80-4120-859a-43fa2b594b1b)<br />
In the challenge, we are limited to a maximum progress of `15%` per day. However, by the third day, we only reach `45%`, which isn't enough to prevent the asteroid from hitting Earth, resulting in a loss.<br />
![image](https://github.com/user-attachments/assets/62a62a96-db1e-4944-9791-9e9a3918181a)<br />
Interestingly, if we input `-200 days` instead of `1 day`, the system accepts it, allowing us to reach `100%` progress before the asteroid hits on the third day. However, to prevent the population from decreasing further, we must continue inputting negative values for the days. This ensures the population stays fixed at `10,000`, allowing us to win the challenge and getting the flag.<br />

![image](https://github.com/user-attachments/assets/afac1180-2fe7-46d1-bc27-5227ccbbfc46)



## Challenge3
Name : `SPACE ADVENTURE` <br />
Points :120 <br />
Description : 
>Just Try And Try And Tryyyyyyyyyyyy from here : `nc 151.80.133.55 9999` <br />

Solution : 	<br />
In this Challenge we need to try all integers between `10` and `80` to get the flag , and inputing all this number one by one will take a lot of times .<br />
![image](https://github.com/user-attachments/assets/2ed76311-ba3b-4c5c-8493-cd794e27a25c)<br />
So we gonna write a python script that connect to `151.80.133.55 9999` and try by it self all this number to find the flag : <br />
Here is my Py Script : <br />
```py
from pwn import *

# Connect to the server
server_ip = "151.80.133.55"
server_port = 9999

# Initialize the connection
conn = remote(server_ip, server_port)

# Receive the prompt message
conn.recvuntil("Enter your launch coordinates (10-80): ")

# Function to send coordinates and check the response
def send_coordinates():
    
    for i in range(10,81):
        conn.sendline(str(i))  # Send the current integer as a string
        
        # Receive the server's response
        response = conn.recvline().decode().strip()  
        
        # Check if the response indicates the correct input
        if "wrong coordinates!" in response:
            #print("Wrong coordinates! Trying next...\n")
            pass
        else:
            if ("SECURINETSISITCOM{" in response) == True:
                print("\n\n\n")
                print("Correct coordinate! Message received:", response)
                print("\n\n\n")
                break  # Exit if the correct response is found

# Call the function to start sending coordinates
send_coordinates()

# Close the connection after we're done
conn.close()
```
<br />

![image](https://github.com/user-attachments/assets/90cd0299-e7d3-43fb-85da-8e8dd83c28fc)



## Challenge4
Name : `Cotisation ;)` <br />
Points :9 <br />
Description :<br />
What is the name of the security club for which you haven't paid the membership fee, huh? ;) <br />
Ty 5alsssssss ;)<br />
The flag will be: `SECURINETSISITCOM{CLUB-NAME_HIS COTISATION in DT}` <br />
Example: `SECURINETSISITCOM{ZEBRACLUB_20DT}` <br />
Solution : 	<br />
`SECURINETSISITCOM{SECURINETS_10DT}`<br />


## Challenge5
Name : `Discord1` <br />
Points :300 <br />
Description : <br />
>Join our Discord community and claim the flag! Click here to join: `https://discord.gg/rsu5AqUY`


Solution : 	<br />
![image](https://github.com/user-attachments/assets/8c53bff3-a9db-43af-8f65-d4c36ec8e973)<br />

Lets try to see , maybe this text hide some characteres inside of it .<br />
This  [Website](https://330k.github.io/misc_tools/unicode_steganography.html) could help decoding zero width character <br />

![image](https://github.com/user-attachments/assets/f9daff65-8e59-4653-963d-39ee477679d5)

`SECURINETSISITCOM{w3lc0m3_t0_0ur_d1sc0rd}`


## Challenge6
Name : `Discord2` <br />
Points :350 <br />
Description : <br />
>Join our Discord server to uncover the second flag! Don’t miss out—click here: `https://discord.gg/rsu5AqUY`

Solution : 	<br />
In this challenge, we needed to find a hidden flag in a SECURINETS Discord server. By installing `BetterDiscord` and using the `"ShowHiddenChannels"` plugin, we revealed hidden channels that were otherwise inaccessible by member. 



















