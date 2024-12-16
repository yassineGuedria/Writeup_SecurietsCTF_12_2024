# Here is my Forensic Solution
- [Challenge1](#challenge1)
- [Challenge2](#challenge2)
- [Challenge3](#challenge3)

---
## Challenge1
Points :150 <br />
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
Details
## Challenge3
Details 

