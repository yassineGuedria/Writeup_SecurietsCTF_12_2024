![image](https://github.com/user-attachments/assets/75ad473c-1c2e-4595-940d-d2854a55ab42)# Here is my Web Solution
- [R3qu3ST](#challenge1)
- [PHP Sh1t](#challenge2)
- [SSTI ?](#challenge3)
- [ROBOT DOG](#challenge4)
- [BF](#challenge5)
- [Birraa333](#challenge6)


---
## Challenge1

![image](https://github.com/user-attachments/assets/dc7baf2a-2b08-4e09-8efe-0ebba41cb1ed)

Solution : <br />

![image](https://github.com/user-attachments/assets/0f3a10fe-28ec-40e2-ad97-6310da3d1ea2)

There is inly the first part of the flag , and to retreave all part of it we gonna use a python script that send all type of request methodes to `151.80.133.55:9000`. <br />
Here a [Link](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) if u want to know more about `HTTP Request Methodes`<br />
And here is the Python Script : 

```py
import requests

url = "http://151.80.133.55:9000/"

methods = [
    "GET", "HEAD", "POST", "PUT", "DELETE", "OPTIONS", "PATCH"
]

flag_parts = []



def send_request(method):
    try:

        if method == "HEAD":
            response = requests.head(url)
        elif method == "OPTIONS":
            response = requests.options(url)

        else:
            response = requests.request(method, url)


        if response.status_code == 200:
            print(f"{method}: {response.text}")
            flag_parts.append(response.text.replace("Flag Part: ", "").strip())
        else:
            print(f"{method}: Failed with status code {response.status_code}")
    except Exception as e:
        print(f"{method}: Error - {str(e)}")


for method in methods:
    send_request(method)


print("\nFull Flag:")
print("".join(flag_parts))
```


![image](https://github.com/user-attachments/assets/3819bdff-6542-43b8-a796-b28a78d296e9)


## Challenge2

![image](https://github.com/user-attachments/assets/0bbb785c-5e6a-499e-a832-9c695652facf)

Solution : <br />

![image](https://github.com/user-attachments/assets/a5969b86-63bc-4792-ad78-2646248a67c3)
![image](https://github.com/user-attachments/assets/8247a5cc-fa2c-467a-967c-ad64fa908ea6)
![image](https://github.com/user-attachments/assets/3ead660f-ce74-4e4b-8f6c-a85c53f6332a)




## Challenge3

![image](https://github.com/user-attachments/assets/6915b173-09b4-476f-b1d9-cec99b56c117)

Solution : <br />
NOT YET

## Challenge4

![image](https://github.com/user-attachments/assets/ad6b56c5-6b19-4274-bc3c-8e9cab3e258a)


Solution : <br />
NOT YET

## Challenge5

![image](https://github.com/user-attachments/assets/fdbec913-c51b-43fb-a084-ee5f99b14171)


Solution : <br />
NOT YET


## Challenge6

![image](https://github.com/user-attachments/assets/0dbb4825-44ad-4d6a-b9a2-0de8a6044b38)


Solution : <br />
NOT YET
