![image](https://github.com/user-attachments/assets/7f648b89-f5ed-4e96-b68d-1b0b6bd562a6)# Here is my Forensic Solution
- [FERX TRIEX](#challenge1)
- [Incognito XD](#challenge2)
- [WH3R3 1S M3](#challenge3)
- [Cicada-3301](#challenge4)

---
## Challenge1
Name: `FERX TRIEX` <br />
Points :500 <br />
Description : <br />
file : 	[oussema _was_here.pdf](oussema-_was_here.pdf) <br />
Solution : 	<br />
i already tried to do bunch of commands but nothing works<br />
>$ exiftool oussema _was_here.pdf<br />
>$ strings oussema _was_here.pdf | grep SECURINETSISITCOM<br />
>$ binwalk oussema _was_here.pdf<br />

but it was a Xref pdf that hide an image inside it and require a script to output the image from the pdf 
and here is my python script:
```py
import pymupdf as UmPDF

CHALL_PDF = 'oussema _was_here.pdf'
SOLVE_IMG = 'flag.png'

with UmPDF.open(CHALL_PDF) as file:
    with open(SOLVE_IMG, 'wb') as image_f:
        chunks = []
        xreflen = file.xref_length()  # length of objects table
        for xref in range(20, xreflen):
            if stream := file.xref_stream(xref):
                chunks.append(stream)

        for chunk in chunks:
            image_f.write(chunk)
```
result : 
![flag](https://github.com/user-attachments/assets/3e3a1619-01c9-4cc7-a9d1-bd9f2cc78651)


## Challenge2
![image](https://github.com/user-attachments/assets/9728e39a-0533-4b44-bc98-16344e80c35f)

File : [Foren-easy.pcapng](Foren-easy.pcapng)  <br />
Solution : 	<br />
In this challenge, we analyzed `Foren-easy.pcapng` using `Wireshark`. <br />
First, we exported objects under `HTTP` and found a file, `readme.md`, which contained the flag.<br /> 
![image](https://github.com/user-attachments/assets/4fdd16c3-dc41-4870-ac78-8993f062d57a)
![image](https://github.com/user-attachments/assets/bc33ed1d-1411-4eb2-b5a1-4a4a62270ba5)
![image](https://github.com/user-attachments/assets/8586535f-af6d-4e31-8ad7-303a472b27cd)

Alternatively, using `Ctrl + F` to search for the flag pattern `SECURINETSISITCOM` in the packet data also revealed the flag. Both methods successfully retrieved the flag.<br /> 

![image](https://github.com/user-attachments/assets/7f139e9e-98c7-46ad-9baf-ab48134b3e83)


## Challenge3
![image](https://github.com/user-attachments/assets/bb74e8de-38a9-4dd2-9f24-ce7e926580e3)


File : [where_is_me.zip](where_is_me.zip)  <br />
Solution : 	<br />
In this challenge, we have zip file with password to unzip it, when we look at challenge description we find "Maybe the Author". <br />
So we can try to input Authors names as password: <br />
`Jarbou3`,`Kanzu`,`King`,`Black_Shadow`<br />
We found out that `Jarbou3` is the password to unzip this file . <br />

![image](https://github.com/user-attachments/assets/18f62113-d56c-45e8-810b-48dfbbf76baa)

The file conatins 100 txt files inside of it ,and only one of them contain the flag . 

So i executed this command that show all files in my directory , prints their content and grep specific flag pattern

![image](https://github.com/user-attachments/assets/17266f9e-d930-4f82-b3ab-a33de5e50339)



## Challenge4
![image](https://github.com/user-attachments/assets/7e715c2f-91e6-4217-8acb-c63b52074322)
File : [where_is_me.zip](where_is_me.zip)  <br />
Solution : 	<br />
1. Use `steghide` with empty password to reveal hidden zip file , and unzip it to get 3 files.

![image](https://github.com/user-attachments/assets/55377822-05a4-48db-9eb9-919230d5cfbb)
![image](https://github.com/user-attachments/assets/306e8e4c-80a0-473a-86af-67fae8f313de)

2. U gonna find the first part of the flag `c2VjdXJpbmV` in `secret message.txt` , and there is a cypher decrepted in rot13 in `stage_2`

![image](https://github.com/user-attachments/assets/f10d174f-06bf-4ac0-b78e-26097c1d9062)

![image](https://github.com/user-attachments/assets/701ee625-cf63-4902-8d48-3ef1e0375047)

3. U have now the second part of the flag `0c3szbmRfMG`, and a [link](https://mega.nz/file/p1AFkAqD#MfggOmi8yNaPuFHK8wtZdetr8L_mjcAvaUtQEwiMQMQ) contain another zip file called `secret2.zip`

![image](https://github.com/user-attachments/assets/ffada21c-6adc-44f9-96a5-919a0d2ec405)

4.The `hint.txt` tell u to seach for car model with this plate license `6656TU195` to get the password of  `Stage_4.zip`

![image](https://github.com/user-attachments/assets/0b356724-1a9c-40ed-9457-2ed4e308f2c9)

5. To find car model u can use this [website](https://vidange.tn/)

![image](https://github.com/user-attachments/assets/1260d828-f1a6-42e6-a0c8-2d1e1a9fd86e)

![image](https://github.com/user-attachments/assets/cc332391-fd9d-43fa-888e-dbf76b7db1ce)

![image](https://github.com/user-attachments/assets/3cdfe29f-9334-4f59-9e60-5e3c9f136c13)

6. U have now the third part of the flag `ZfdGgzXzRkd` ,and your mission is to get the final flag by decrypting this cypher `Zryoiu: nPnlUXmD30` ; the hints indicate that this cypher is encoded with `Vigenere` and the key have could be found in stage-1 .

![image](https://github.com/user-attachments/assets/a48f68bb-03df-4b4c-bb49-2e7dd011c52d)

7. U need to go back to Stage-1 to find anythink that could be a password

![image](https://github.com/user-attachments/assets/9da98e53-80f1-4f8b-be75-a486aaf00d09)

8. As u see there is a file called `password is incorrect` that we never use , maybe the word `incorrect` is the key .

![image](https://github.com/user-attachments/assets/ad543ace-e534-4157-a9ce-2c82f7867437)

9. Congratulations now u have all the 4 parts of the flag , `c2VjdXJpbmV_0c3szbmRfMG_ZfdGgzXzRkd_jNudHVyM30` decode them from `base 64` and u gonna have the flag

![image](https://github.com/user-attachments/assets/960824db-c795-417c-b5a3-15238ab0751f)






