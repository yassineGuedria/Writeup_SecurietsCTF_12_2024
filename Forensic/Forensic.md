# Here is my Forensic Solution
- [Challenge1](#challenge1)
- [Incognito XD](#challenge2)
- [WH3R3 1S M3](#challenge3)
- [Challenge3](#challenge4)

---
## Challenge1
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









## Challenge6
![image](https://github.com/user-attachments/assets/7e715c2f-91e6-4217-8acb-c63b52074322)
Details



## Challenge7

![image](https://github.com/user-attachments/assets/26b0cd4e-2a5c-4378-9087-c3020e9057e4)
Details


