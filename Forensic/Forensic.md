# Here is my Forensic Solution
- [Challenge1](#challenge1)
- [Challenge2](#challenge2)
- [Challenge3](#challenge3)

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
![image](https://github.com/user-attachments/assets/26b0cd4e-2a5c-4378-9087-c3020e9057e4)

details

## Challenge3
![image](https://github.com/user-attachments/assets/7e715c2f-91e6-4217-8acb-c63b52074322)

Details 

## Challenge4
![image](https://github.com/user-attachments/assets/bb74e8de-38a9-4dd2-9f24-ce7e926580e3)

Details 

## Challenge5
![image](https://github.com/user-attachments/assets/67e9a5a3-1cae-4149-a533-69162cd7b642)

Details

## Challenge6
![image](https://github.com/user-attachments/assets/19a6cb60-e6ec-4bbb-a7ba-3f0aeab03c04)
Details

## Challenge7
![image](https://github.com/user-attachments/assets/27d90f4d-e27c-48e8-9b6b-1565e450cb90)

Details


## Challenge7
![image](https://github.com/user-attachments/assets/9728e39a-0533-4b44-bc98-16344e80c35f)

Details


