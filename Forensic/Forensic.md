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
Points :1000 <br />
Description : <br />
file : 	[hello.png](hello.png) [world.jpg](world.jpg) <br />
Solution : 	<br />
To solve this challenge, were given two images, `hello.png` and `world.jpg`, and needed to XOR them to extract the flag .
here is my code :
```py
import cv2

def bitwise_xor_images(image1_path, image2_path):
  try:
    image1 = cv2.imread(image1_path)
    image2 = cv2.imread(image2_path)

    if image1 is None or image2 is None:
      print("Error: Could not read one or both images.")
      return None

    # Resize image2 to match image1's size
    if image1.shape != image2.shape:
      image2 = cv2.resize(image2, dsize=(image1.shape[1], image1.shape[0]))

    result = cv2.bitwise_xor(image1, image2)

    return result

  except Exception as e:
    print(f"An error occurred: {e}")
    return None

if __name__ == "__main__":
  image1_path = "./hello.png"
  image2_path = "./world.jpg"

  result_image = bitwise_xor_images(image1_path, image2_path)

  if result_image is not None:
    cv2.imshow("xored data", result_image)
    cv2.waitKey(0)
    cv2.destroyAllWindows()
```
and here is the flag :
![image](https://github.com/user-attachments/assets/a212e35f-f5e8-4fb8-875a-ac8a1f805ba1)

## Challenge3
Details 

