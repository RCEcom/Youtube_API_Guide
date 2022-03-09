# Youtube_API_Guide
> It is documents to use easy Youtube API.

> Than, You can find only what you want.

# How to find? and How to use?
#### you should follow that my step to use efficient documents.
>#### first) "ctl + f" push and I search that trying to do what I want.
#### ex) "Load Channel.", "Find a channel"
#### ex) 한국어 지원합니다 "채널 불러오기", "채널 찾기"
>#### second) Next also, We can take code sample when code you think is good.
### I hope you  well. :)

# If this is your first time, please take a closer look right below.

---
>## *Fast start*
>> 1. API Key Issued
>> 2. Bulid enviornment to use API
>> 3. Service connect  
>> 4. Simple example
>> 5. Using OAuth to Access User Accounts
  
  
  
>## API Key Issued  
  
    
    


> go in https://console.cloud.google.com/projectselector2/apis/dashboard?pli=1&supportedpurview=project link.   
> ![image](https://user-images.githubusercontent.com/87273590/157449759-ab0fdb25-8700-4201-9b1b-f9f0cf76b3ee.png)  
> click the "Project create"   
> ![image](https://user-images.githubusercontent.com/87273590/157449888-e4b73a9a-9581-4726-8ee5-bbbf65e17f2a.png)   
> project name Write it down.   
> ![image](https://user-images.githubusercontent.com/87273590/157450135-9a97069d-9ad4-4cba-b96e-19ee85a82079.png)  
> Click on Enable API  
> ![image](https://user-images.githubusercontent.com/87273590/157450502-bde5cdd5-9376-4853-84a5-12bf81960fc6.png)   
> there are many Youtube API but, we are to use "Youtube Data API v3"   
> ![image](https://user-images.githubusercontent.com/87273590/157451666-45de8777-6859-4ddc-bbe8-1696a717b1d8.png)   
> Click on "use"   
> ![image](https://user-images.githubusercontent.com/87273590/157451751-b8388cbd-464b-4cdc-8ab8-97dc128c876a.png)   
> We can use API because activate Youtube API.   
> But we need to get a qualification to write the API.   
> ![image](https://user-images.githubusercontent.com/87273590/157452129-708197a2-de11-4624-a81f-2c81e55b36b4.png)   
> ![image](https://user-images.githubusercontent.com/87273590/157452262-053a1a34-3266-4737-b54f-ca82dd66fa19.png)   
> We are to choice public data.   
> and It is better not to show the key value.     


>## Bulid enviornment to use API
> go in https://github.com/googleapis/google-api-python-client link.  
> and  
> ![image](https://user-images.githubusercontent.com/87273590/157454116-66971546-d61d-4806-b1d9-012c0fb38c98.png).  
> Download the package to write the library.   
> ![image](https://user-images.githubusercontent.com/87273590/157454465-d5c19e13-1a0b-4204-b66d-ffad9a4a5996.png).   
> If it is, you are successful.   
> https://googleapis.github.io/google-api-python-client/docs/dyn/youtube_v3.html Please note.  
 
>## Service connect
```python
from googleapiclient.discovery import build
```  

```python
from googleapiclient.discovery import build
API_key = "123123123123"

youtube = build("youtube", "v3", developerKey=API_key)
```  
> service object output and We could perform several functions with that object.

>## Simple example  
> Let's do a simple exercise.  
```python
from googleapiclient.discovery import build
API_key = "(your key)"

youtube = build("youtube", "v3", developerKey=API_key)

request = youtube.channels().list(
                part="statistics",
                forUsername="steve"
        )

respones = request.execute()
print(respones)
```
> What information will the part provide about you?  
> statistics     
> forUsername p is user name about information.
> ![image](https://user-images.githubusercontent.com/87273590/157487199-64abd89c-193e-42c3-aecf-ba12fbd51d49.png)
> List them in order.  
> Number of users viewed on YouTube to date: 281371  
> Number of users subscribed to: 4290  
> Hide user subscriber count: false  
> User Subscribers: 4
> This is just a tutorial, so please find the full-fledged one in the list below :)


>## Using OAuth to Access User Accounts  
> 
---



# API List!
+ 

