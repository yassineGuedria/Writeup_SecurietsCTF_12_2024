# Here is my Cryptography Solutions
- [Challenge1](#challenge1)
- [Challenge2](#challenge2)
- [Challenge3](#challenge3)

---

## Challenge1
Points :150 <br />
Description : <br />
file : 	[Output.txt](Output.txt)  <br />
Solution : 	<br />
We were given an RSA-encrypted flag with the following parameters:

N: Modulus
e: Public exponent (e = 3 in this case)
encFlag: Ciphertext
The goal was to decrypt the flag.

## Challenge2
Points :1000 <br />
Description : <br />
file : 	[hello.png](hello.png) [world.jpg](world.jpg) <br />
Solution : 	<br />




## Challenge3
Points :200 <br />
Description : <br />
file : 	[encflag.txt](encflag.txt) <br />
Solution : 	<br />
we have in this challenge a multi layer cypher and we need to decode it 

>### first , as the last char of this cypher is '=' so maybe it can be a `base64` 

![image](https://github.com/user-attachments/assets/3a88b1ad-70bd-42ed-aabf-b5574f3b138e)

>### lets try to convert this numbers from base64 to `hex`
 
![image](https://github.com/user-attachments/assets/980fb81b-d3e2-4623-ae38-7d1e72c484c0)

>### and now it gives us `binary` numbers  

![image](https://github.com/user-attachments/assets/bc0db4e4-1ecf-4ebc-9107-76be63005275)

>### this time the numbers that we got looks like `decimal` 

![image](https://github.com/user-attachments/assets/fb4a8090-4d86-4e82-939d-15d8e1bb3b8a)

>### and this time this cypher is `rot13` 

![image](https://github.com/user-attachments/assets/706e4e5e-7a61-4948-a1fb-86c4ee18ac13)

#### in this challenge the flag is coded in muli layers , we need to decode the cypher from `base64` to `hex` to `binary` to `decimal` to `rot13` to get the flag
`SECURINETSISITCOM{ROT13-DECIMAL-BINARY-HEX-BASE64}`






