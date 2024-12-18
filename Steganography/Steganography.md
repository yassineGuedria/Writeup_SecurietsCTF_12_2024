# Here is my Steganography Solutions

- [FIXE EM](#challenge1)
- [FIXE EM 2](#challenge2)
- [STEG TN](#challenge3)


---

## Challenge1
Name: `FIXE EM `<br />
Points :100 <br />
Description : <br />
>Reyna is Looking For u in the FIXE , Flag : SECURINETSISITCOM{*__*}

file : 	[Reyna_Fullbody.png](Reyna_Fullbody.png) <br />
Solution : 	<br />
From the flag format `SECURINETSISITCOM{flag}`, I deduced the flag could be found as plaintext. Using the command:<br />

`$ strings Reyna_Fullbody.png | grep SECURINETSISITCOM`<br />

![image](https://github.com/user-attachments/assets/1a8c70c7-f35f-46dd-8db2-f8ef3a9b8f4f)


## Challenge2
Name: `FIXE EM 2`<br />
Points :100 <br />
Description : <br />
>It's F**king EZZZZZZZZZ BROOOOOOOOO!!! Flag : SECURINETSISITCOM{*__*}

file : 	[secret_document.pdf](secret_document.pdf) <br />
Solution : 	<br />
>$ exiftool secret_document.pdf

![image](https://github.com/user-attachments/assets/2026e975-c6da-4676-92f1-dbff24128319)


## Challenge3
Name: `STEG TN`<br />
Points :150 <br />
Description : <br />
>The STEG in Cyber, Not the Same in Tunisia!

file : 	[cute-cat.jpg](cute-cat.jpg) <br />
Solution : 	<br />
I tried various tools like file, `exiftool`, `binwalk`, and `strings` to extract hidden data from the image `cute-cat.jpg`. However, I couldn't find any hidden information using these methods.

The only tool that seemed promising was `Steghide`, which requires a password to extract hidden data. I tried several passwords, including an empty one, but none worked.

Finally, I discovered that the password `"cat"` successfully extracted the hidden file called `secret.txt` that contain the flga decrepted in base 64.

![image](https://github.com/user-attachments/assets/d18f2b57-38fe-488a-945b-f81b7b036f2c)
