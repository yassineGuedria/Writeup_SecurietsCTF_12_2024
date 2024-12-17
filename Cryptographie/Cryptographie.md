# Here is my Cryptography Solutions
- [Challenge1](#RSA-MY-LOVE)
- [Challenge2](#challenge2)
- [Challenge3](#challenge3)
- [Challenge4](#DO-U-KNOW-ELLIOT-FROM-MR.ROBOT-,-CAN-U-XOR-HIM?)

---

## RSA MY LOVE
Points :500 <br />
Description :mmm do you know that RSA is my initial step in learning cryptography challenges in CTF? any way, can you break this for me? <br />
file : 	[Output.txt](Output.txt)  <br />
Solution : 	<br />
We were given an RSA-encrypted flag with the following parameters:<br />

N: Modulus<br />
e: Public exponent (e = 3 in this case)<br />
encFlag: Ciphertext<br />
The goal was to decrypt the flag.<br />
![image](https://github.com/user-attachments/assets/6ee71002-bb05-4328-8348-6070d01e7d60)

the code i used in this case is : <br />
```py
import gmpy2

# Given RSA parameters
N = 18814840635346619874425333469811897321549418263501570889282825750834515074675420955536024872473333925100162290869450343342196370005147241590450746764679485718567750837860298441879336049949463769103929953264633072242523089509554532420960226194229074889893991993272393955287647019173019565996826761031489963195126291001577851134834313095727805927258826762839259238704853071924049305921348548805171136582998855037946513227862183246591156434241274337978149248881248098712196426195343743140711782990404627731190157041047720437406870278036078843043167368486244024032010310184530070850162225094426996919028658409155918085541
e = 0x3
encFlag = 26572349774532122558413822660787565800876859961042748864197505662294319821137420537449406034432755970252620682951620140376826571119571396577525308224469379695704886151366719681917316926664475491403254419941927069176375066837735027264004604420524982390706651874487308796663467648818962491218331170345389279578813057125

# Check if c < N (ciphertext smaller than modulus)
if encFlag < N:
    # Attempt to find the cubic root of the ciphertext
    m, exact = gmpy2.iroot(encFlag, e)
    if exact:
        # Convert the result to a string (decoded plaintext)
        print("Decrypted plaintext (flag):", bytes.fromhex(hex(int(m))[2:]).decode())
    else:
        print("Cubic root not exact; decryption failed.")
else:
    print("Ciphertext larger than modulus. Decryption not directly possible.")

```

and the flag is :<br />
![image](https://github.com/user-attachments/assets/e0b93355-1015-4ec8-89eb-45322bf9a66b)





## Challenge2
Points :200 <br />
Description : <br />
file : 	[assembly.asm](assembly.asm)  <br />
Solution : 	<br />
We have assembly code in this challenge .

First thing i did is i converted the `assembly` code to `C language`. <br />
I used this [Website](https://www.codeconvert.ai/assembly-to-c-converter) to do the convertation. <br />
And then i executed the `C` code to get this cypher :  <br />
>awqg`{|wfa{a{fq}i[M^]DWMSAA_WP^Ko

![image](https://github.com/user-attachments/assets/53054f15-c3ae-4ff1-8ebf-fe3c92f5a8a5)

<br />

### Thanks to the CyberChef `magic` recipe that help me identify the cypher type ,which is `XOR` .

<br />

![image](https://github.com/user-attachments/assets/09904607-c8da-4b55-8c1a-ed97bb849802)


## Challenge3
Points :200 <br />
Description : <br />
file : 	[encflag.txt](encflag.txt) <br />
Solution : 	<br />
we have in this challenge a multi layer cypher and we need to decode it 

>### First , as the last char of this cypher is '=' so maybe it can be a `base64` <br />

![image](https://github.com/user-attachments/assets/3a88b1ad-70bd-42ed-aabf-b5574f3b138e)<br />

>### Lets try to convert this numbers from base64 to `hex`<br />
 
![image](https://github.com/user-attachments/assets/980fb81b-d3e2-4623-ae38-7d1e72c484c0)<br />

>### And now it gives us `binary` numbers  <br />

![image](https://github.com/user-attachments/assets/bc0db4e4-1ecf-4ebc-9107-76be63005275)<br />

>### This time the numbers that we got looks like `decimal` <br />

![image](https://github.com/user-attachments/assets/fb4a8090-4d86-4e82-939d-15d8e1bb3b8a)<br />

>### And finally this cypher is `rot13` <br />

![image](https://github.com/user-attachments/assets/706e4e5e-7a61-4948-a1fb-86c4ee18ac13)<br />
<br />
#### In this challenge the flag is coded in muli layers , we need to decode the cypher from `base64` to `hex` to `binary` to `decimal` to `rot13` to get the flag
`SECURINETSISITCOM{ROT13-DECIMAL-BINARY-HEX-BASE64}`



## DO U KNOW ELLIOT FROM MR.ROBOT , CAN U XOR HIM?
Points :1000 <br />
Description : I have hidden two interesting images using XOR with the same secret key , so they are not visible!  <br />
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






