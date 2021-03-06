# Youtube_API_Guide
> It is documents to use easy Youtube API.

>This document guides you to write your own Youtube API.

# If this is your first time, please take a closer look right below.

---
>## *Fast start*
>> 1. API Key Issued
>> 2. Bulid enviornment to use API
>> 3. Service connect  
>> 4. Simple example
>> 5. Using OAuth to Access User Accounts  
>> 6. Write OAuth effectively
  
  
  
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
> User Subscriptions: 4290  
> Hide user subscriber count: false  
> Number of user images: 4
> This is just a tutorial, so please find the full-fledged one in the list below :)


>## Using OAuth to Access User Accounts  
> To access data about real users, you need to authenticate with OAuth.  
> Let's look at the following sample code.  
```python
from googleapiclient.discovery import build
API_key = "(your API KEY)"

youtube = build("youtube", "v3", developerKey=API_key)
request = youtube.channels().list(
                part="contentDetails",
                forUsername="schafer5"
        )


respones = request.execute()

print(respones)
```  
> Get the user's playlist ID.
> If OAuth authentication is not performed, only basic information can be viewed.  
```python
'likes': '', 'uploads': 'UUCezIgC97PvUuR4_gbFUs5g'}}}]}
```  
```python
{'kind': 'youtube#playlistItemListResponse', 'etag': 'CG3odeN9t4JPibirQ8aBIwYq8gA', 'nextPageToken': 'EAAaBlBUOkNBVQ', 'items': [{'kind': 'youtube#playlistItem', 'etag': 'ZamMnwWX4mu0an36qlsYH3MSSAg', 'id': 'VVVDZXpJZ0M5N1B2VXVSNF9nYkZVczVnLnZRUUVhU25RX2Jz', 'status': {'privacyStatus': 'public'}}, {'kind': 'youtube#playlistItem', 'etag': 'g8B_7Mc87o6BgvstV2vRopAhVls', 'id': 'VVVDZXpJZ0M5N1B2VXVSNF9nYkZVczVnLjFLT19IWnRIT1dJ', 'status': {'privacyStatus': 'public'}}, {'kind': 'youtube#playlistItem', 'etag': 'hPPdKXKLketdQ71g4SGdrb0gFqo', 'id': 'VVVDZXpJZ0M5N1B2VXVSNF9nYkZVczVnLmNvWmJPTTZFNDdJ', 'status': {'privacyStatus': 'public'}}, {'kind': 'youtube#playlistItem', 'etag': 'daxFi1dbhLeRmrwszyAh042lvTw', 'id': 'VVVDZXpJZ0M5N1B2VXVSNF9nYkZVczVnLnRoNV85d29GSm1r', 'status': {'privacyStatus': 'public'}}, {'kind': 'youtube#playlistItem', 'etag': 'EJVhXB1vj-nstLtnZAHUq_uyAGk', 'id': 'VVVDZXpJZ0M5N1B2VXVSNF9nYkZVczVnLlJPNkp4RE9Wd0xR', 'status': {'privacyStatus': 'public'}}], 'pageInfo': {'totalResults': 230, 'resultsPerPage': 5}}
```  
> In order to see various undisclosed information, not public information, such as the following, you need to authenticate.  
>![image](https://user-images.githubusercontent.com/87273590/157681346-0c4879ef-6380-4d2a-9da8-04148418c04f.png)  
> Click On "OAuth client ID create"
> ![image](https://user-images.githubusercontent.com/87273590/157681619-cf137280-acc7-40a1-8fb7-1b2d01fb7706.png)  
> Click On "Consent screen configuration"    
> ![image](https://user-images.githubusercontent.com/87273590/157681865-1d9a8de5-e554-45c0-9a19-72af8393935e.png)  
> We will make it accessible to everyone.  
> ![image](https://user-images.githubusercontent.com/87273590/157682161-154a9aeb-adaf-4f65-9a8f-f8cf0a04c06a.png)  
> We'll just write your name down and we'll make it for you. Right now.  
> ![image](https://user-images.githubusercontent.com/87273590/157682464-798cd7de-795a-439b-ab17-34d346956897.png)  
> After that, press OAuth Client create ID again to enter, and the following screen will appear.  
> There is no application for Python scripts. So we will run it as a web application.  
> ![image](https://user-images.githubusercontent.com/87273590/157683110-3c291fab-3636-4462-acff-3eef50d5252a.png)  
> set to localhost  
> ![image](https://user-images.githubusercontent.com/87273590/157683521-91ae54ee-f3ac-4233-9311-b9fa0ac8f5d0.png)  
> Then, download the json file.  
> ![image](https://user-images.githubusercontent.com/87273590/157683733-bcf8ef4c-cea0-4836-b564-ea096b4e6e38.png)  
> Edits the file name.  
> ![image](https://user-images.githubusercontent.com/87273590/157683936-1f6794d9-b3f0-45dd-9d4b-f70869483d6e.png)  
> json file to your working directory.  
```python
pip install google_auth
pip install google-auth-oauthlib
```  
> Enter the code above to easily access Oauth authentication.  
```python
import os
from google_auth_oauthlib.flow import InstalledAppFlow
from google.auth.transport.requests import Request
from googleapiclient.discovery import build

#Get Oauth Certificate Access File
flow = InstalledAppFlow.from_clients_secrets_file("client_secrets.json")

API_key = "(your API KEY)"

youtube = build("youtube", "v3", developerKey=API_key)
request = youtube.playlistItems().list(
                part="status",
                playlistId="UUCezIgC97PvUuR4_gbFUs5g"
        )


respones = request.execute()

print(respones)
```  
> If you have imported the OAulth protocol, you need to know the scope of the access (how far it is allowed).  
> ![image](https://user-images.githubusercontent.com/87273590/157688431-4113d832-2019-4680-aa73-f0d765f7a4b5.png)  
> Depends on the purpose, but we'll only narrow it down to verifying your YouTube account.  
> ![image](https://user-images.githubusercontent.com/87273590/157689147-2449bd41-c6ac-48ed-a5cb-cbf4c89ebbe7.png)  
> Would you like to display a message when accessing in the future?  
> and The run_local_server code connects to the local server and obtains user rights.  
```python
import os
from google_auth_oauthlib.flow import InstalledAppFlow
from google.auth.transport.requests import Request
from googleapiclient.discovery import build
     
#Get Oauth Certificate Access File
#scopes : The scopes url pursued by each function is different.
flow = InstalledAppFlow.from_client_secrets_file("client_secrets.json", scopes=["https://www.googleapis.com/auth/youtube.readonly"])

flow.run_local_server(port=8080, prompt="consent")

credentials = flow.credentials
print(credentials.to_json())

"""
API_key = ""

youtube = build("youtube", "v3", developerKey=API_key)
request = youtube.playlistItems().list(
                part="status",
                playlistId="UUCezIgC97PvUuR4_gbFUs5g"
        )


respones = request.execute()

print(respones)
"""
```  
> By setting it to "constent" in the prompt parameter, it gives the convenience of not having to check it next time.    
> ![image](https://user-images.githubusercontent.com/87273590/157693430-edd641e3-c85d-4956-ad34-8075aaa6ed83.png)  
> If it pops up with me, add user access list  
> ![image](https://user-images.githubusercontent.com/87273590/157693530-85dac2c6-d532-4232-86a0-3945a2e5fc98.png)  
> ![image](https://user-images.githubusercontent.com/87273590/157693589-050283f4-d9e1-40fa-a758-db211b1147b9.png)  
> If it pops up like this, it's a success! good job  
> Now we don't have to use the existing API.  
```python
import os
from google_auth_oauthlib.flow import InstalledAppFlow
from google.auth.transport.requests import Request
from googleapiclient.discovery import build
     
#Get Oauth Certificate Access File
flow = InstalledAppFlow.from_client_secrets_file("client_secrets.json", scopes=["https://www.googleapis.com/auth/youtube.readonly"])

flow.run_local_server(port=8080, prompt="consent")

credentials = flow.credentials


youtube = build("youtube", "v3", credentials=credentials)

request = youtube.playlistItems().list(
                part="status",
                playlistId="UUCezIgC97PvUuR4_gbFUs5g"
        )


respones = request.execute()

print(respones)
```
> As in the code above, pass it as credentials=credentials instead of passing it as APK_KEY.  
```python
import os
from google_auth_oauthlib.flow import InstalledAppFlow
from google.auth.transport.requests import Request
from googleapiclient.discovery import build
     
#Get Oauth Certificate Access File
flow = InstalledAppFlow.from_client_secrets_file("client_secrets.json", scopes=["https://www.googleapis.com/auth/youtube.readonly"])

flow.run_local_server(port=8080, prompt="consent", authorization_prompt_message='')

credentials = flow.credentials


youtube = build("youtube", "v3", credentials=credentials)

request = youtube.playlistItems().list(
                part="status, contentDetails",
                playlistId="UUCezIgC97PvUuR4_gbFUs5g"
        )


respones = request.execute()

for item in respones["items"]:
    print(item["contentDetails"]["videoId"])

print(respones)
```
> Using it a bit more, get the playlist videoID value. 5 is the default setting, so you need to increase it further.  
> So the tutorial is over. Use a variety of APIs to create what you want!  

>## Write OAuth effectively  
```python
flow.run_local_server(port=8080, prompt="consent", authorization_prompt_message="")
```  
> authorization_prompt_message="" Add the corresponding command to prevent the output window from appearing long.  
> As you may not have noticed, access tokens expire quickly.  
> So, we will simply understand how OAuth simple works, and write an automated script to get the expired token back.  
> ![image](https://user-images.githubusercontent.com/87273590/157895678-ab7a1efa-f851-4a71-90da-f92c7de99b4d.png)  
> First we request a token, and the Google servers send me back an access authorization code for the user.  
> Next, in case the token expires, we write code to retrieve the token again and send it, and that amount comes from the server.  
> That's what we've hit the code for now, and from now on, let's write an automated script that checks if it's expired and refreshes the token ourselves.  
```python
credentials = None
```  
> The authentication object will be put into a variable then when certain conditions are all met.  
```python
import os
import pickle
from google_auth_oauthlib.flow import InstalledAppFlow
from google.auth.transport.requests import Request
from googleapiclient.discovery import build

#Get Oauth Certificate Access File
flow = InstalledAppFlow.from_client_secrets_file("client_secrets.json", 
    scopes=["https://www.googleapis.com/auth/youtube.readonly"]
            )

flow.run_local_server(port=8080, prompt="consent", authorization_prompt_message="")

credentials = None

# token.pickle stores the user's credentials from previously successful logins
if os.path.exists('token.pickle'):
    print('Loading Credentials From File...')
    with open('token.pickle', 'rb') as token:
        credentials = pickle.load(token)

credentials.to_json()
```  
> First check if the token exists.  
```python
import os
import pickle
from google_auth_oauthlib.flow import InstalledAppFlow
from google.auth.transport.requests import Request
from googleapiclient.discovery import build

credentials = None

# token.pickle stores the user's credentials from previously successful logins
if os.path.exists('token.pickle'):
    print('Loading Credentials From File...')
    with open('token.pickle', 'rb') as token:
        credentials = pickle.load(token)

# If there are no valid credentials available, then either refresh the token or log in.
if not credentials or not credentials.valid:
    if credentials and credentials.expired and credentials.refresh_token:
        print('Refreshing Access Token...')
        credentials.refresh(Request())
    else:
        print('Fetching New Tokens...')
        flow = InstalledAppFlow.from_client_secrets_file(
            'client_secrets.json',
            scopes=[
                'https://www.googleapis.com/auth/youtube.readonly'
            ]
        )

        flow.run_local_server(port=8080, prompt='consent',
                              authorization_prompt_message='')
        credentials = flow.credentials

        # Save the credentials for the next run
        with open('token.pickle', 'wb') as f:
            print('Saving Credentials for Future Use...')
            pickle.dump(credentials, f)

```  
> Let me explain that code. Simply put, it just checks if the credential is invalid or doesn't exist, and runs the code accordingly.  
> Don't try to analyze this code in detail. This is an essential part to write in the future.  
```python
import os
import pickle
from google_auth_oauthlib.flow import InstalledAppFlow
from google.auth.transport.requests import Request
from googleapiclient.discovery import build

credentials = None
    
# token.pickle stores the user's credentials from previously successful logins
if os.path.exists('token.pickle'):
    print('Loading Credentials From File...')
    with open('token.pickle', 'rb') as token:
        credentials = pickle.load(token)

# If there are no valid credentials available, then either refresh the token or log in.
if not credentials or not credentials.valid:
    if credentials and credentials.expired and credentials.refresh_token:
        print('Refreshing Access Token...')
        credentials.refresh(Request())
    else:
        print('Fetching New Tokens...')
        flow = InstalledAppFlow.from_client_secrets_file(
            'client_secrets.json',
            scopes=[
                'https://www.googleapis.com/auth/youtube.readonly'
            ]
        )

        flow.run_local_server(port=8080, prompt='consent',
                              authorization_prompt_message="")
        credentials = flow.credentials

        # Save the credentials for the next run
        with open('token.pickle', 'wb') as f:
            print('Saving Credentials for Future Use...')
            pickle.dump(credentials, f)
    
youtube = build("youtube", "v3", credentials=credentials)

request = youtube.playlistItems().list(
                part="status, contentDetails",
                playlistId="(your uploads ID)",
                maxResults=30
        )


respones = request.execute()

for item in respones["items"]:
    print(item["contentDetails"]["videoId"])
```  
> This is the final code.  
---  



# YouTube API simple usage :)  
> 1)[??????????????????????????????id??????](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#read-before-use)    
> 2)[???????????????????????????????????????????????????,??????????????????,????????????????????????,?????????????????????](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#read-before-use-1)  
> 3)[???????????????id??????](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#read-before-use-2)  
> 4)[??????????????????????????????????????????????????????](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#read-before-use-3)  
> 5)[??????????????????????????????????????????](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#read-before-use-4)  
> 6)[???????????????????????????????????????????????????](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#read-before-use-5)  

# How to find and write APIs yourself.  
>![image](https://user-images.githubusercontent.com/87273590/158064905-4eeb3276-845c-4fbf-95f9-adadedccc861.png)  
>Click to select the desired function  
>![image](https://user-images.githubusercontent.com/87273590/158064952-935c4fd7-c20e-4e90-bfaf-1bd95ce9e748.png)  
>![image](https://user-images.githubusercontent.com/87273590/158065031-7378b31e-5029-4ab7-bf6f-673cae31a193.png)  
>![image](https://user-images.githubusercontent.com/87273590/158065036-5007c771-ff62-483a-a757-3de987b0f9db.png)  
>activities Resource click  
>![image](https://user-images.githubusercontent.com/87273590/158065067-17d9a58e-b2bb-42db-99df-93450938b453.png)  
>Then you can see all the responses for that function. If you want to know more, just scroll down and you will find the explanation.  
>![image](https://user-images.githubusercontent.com/87273590/158065114-53bd882b-815e-4075-bedd-622601ee278f.png)  
# So now let's enjoy.

#[+]Even looking at the parameters, I don't know how to write the code.  
#It is natural. In this case, it is good to see the code provided by the API documentation, but there are many parts that I do not understand.  
#![image](https://user-images.githubusercontent.com/87273590/158387543-6759317e-320b-41fa-b60b-71904e5586af.png)  
#It's okay though. We take only what we want!  
#![image](https://user-images.githubusercontent.com/87273590/158387684-cc7b149a-03e4-45e9-a0ff-c477f1445105.png)  
#![image](https://user-images.githubusercontent.com/87273590/158387713-790d39a5-c758-4c56-87bb-9e11c5e76289.png)  
#There are two functions. One is a service connection, and the other is a code that directly executes the video uploading code.  
#Now, let's write code based on this. (You must have some ability to read code)  
```python
import os
from google_auth_oauthlib.flow import InstalledAppFlow
from google.auth.transport.requests import Request
from googleapiclient.discovery import build
from apiclient.http import MediaFileUpload
     
#Get Oauth Certificate Access File
flow = InstalledAppFlow.from_client_secrets_file("client_secrets.json",
                                                 scopes=["https://www.googleapis.com/auth/youtube.upload"])

flow.run_local_server(port=8080, prompt="consent")

credentials = flow.credentials


youtube = build("youtube", "v3", credentials=credentials)
```
#We already had the code to connect the service.  
#![image](https://user-images.githubusercontent.com/87273590/158393535-f09bebad-b976-4ddc-a36b-ec0d202cc29c.png)  
#And we can basically send something like the picture above as the request body.  
#You don't have to write them all down. Write down if necessary.  
```python
request_body = {
        'snippet' : {
            'title' : 'Test Uploading',
            'description' : 'NULL :)',
            'tags' : ['LOL', 'minecreaft', 'GTA5'],
            'categoryId' : 20
        },
        'status' : {
            'privacyStatus' : 'public',
            'publicStatsViewable' : True
        },
        
    }
```
#I added this:  
```python
insert_request = youtube.videos().insert(
        part='snippet, status',
        body=request_body,
        media_body=MediaFileUpload(file, chunksize=-1, resumable=True)
    ).execute()
```
#As for the video parameter, the part value was written for snippet and status, so select two.  
```python
import os
from google_auth_oauthlib.flow import InstalledAppFlow
from google.auth.transport.requests import Request
from googleapiclient.discovery import build
from apiclient.http import MediaFileUpload
     
#Get Oauth Certificate Access File
flow = InstalledAppFlow.from_client_secrets_file("client_secrets.json",
                                                 scopes=["https://www.googleapis.com/auth/youtube.upload"])

flow.run_local_server(port=8080, prompt="consent")

credentials = flow.credentials


youtube = build("youtube", "v3", credentials=credentials)


def initialize_upload(youtube, file):
    request_body = {
        'snippet' : {
            'title' : 'Test Uploading',
            'description' : 'NULL :)',
            'tags' : ['LOL', 'minecreaft', 'GTA5'],
            'categoryId' : 20
        },
        'status' : {
            'privacyStatus' : 'public',
            'publicStatsViewable' : True
        },
        
    }
    insert_request = youtube.videos().insert(
        part='snippet, status',
        body=request_body,
        media_body=MediaFileUpload(file, chunksize=-1, resumable=True)
    ).execute()


initialize_upload(youtube, "Test.MP4")
```
#at all code.
#![image](https://user-images.githubusercontent.com/87273590/158394273-a234d122-be1b-489c-8f2c-b622cf77ed64.png)  
#That's good.  
#Video thumbnails are not selected. Do this yourself.  





# This is the prep code before writing the activity-related API.
```python
youtube = build("youtube", "v3", developerKey=API_key)


request = youtube.activities().list(
                part="snippet,contentDetails",
                channelId="(your channelId)",
        )


respones = request.execute()
```  

>If you want to use the OAuth function, change it as follows.  
```python
youtube = build("youtube", "v3", credentials=credentials)
```



>If you want to increase the result(The initial return value is 5)  
```python
request = youtube.activities().list(
                part="snippet,contentDetails",
                channelId="(your channelId)",
                maxResults=(number)
        )
```
  
  
  

# [Read Before Use](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#:~:text=This%20is%20the%20prep%20code%20before%20writing%20the%20activity%2Drelated%20API.)  
>OAuth not enabled  
```python
#code you want.
for item in respones["items"]:
    print(item["contentDetails"]["upload"]["videoId"])
```  


>OAuth enabled(Link with my account)  
>"mine=True"If this happens, instead of entering the channel ID, it recognizes the token and finds a value for it.   
```python
request = youtube.activities().list(
                part="snippet,contentDetails",
                mine=True
        )
```   
  
  
```python
#code you want.
for item in respones["items"]:
    print(item["contentDetails"]["upload"]["videoId"])
```  



# [Read Before Use](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#:~:text=This%20is%20the%20prep%20code%20before%20writing%20the%20activity%2Drelated%20API.)  
>OAuth not enabled  
```python
#code you want.
for item in respones["items"]:
    print(item["snippet"]["description"])
```  


>OAuth enabled(Link with my account)  
>"mine=True"If this happens, instead of entering the channel ID, it recognizes the token and finds a value for it.   
```python
request = youtube.activities().list(
                part="snippet,contentDetails",
                mine=True
        )
```   
  
  
```python
#code you want.
for item in respones["items"]:
    print(item["snippet"]["description"])
```  
  
  
# [Read Before Use](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#:~:text=This%20is%20the%20prep%20code%20before%20writing%20the%20activity%2Drelated%20API.)  
>OAuth not enabled  
```python
#code you want.
for item in respones["items"]:
    print(item["snippet"]["channelId"])
```  


>OAuth enabled(Link with my account)  
>"mine=True"If this happens, instead of entering the channel ID, it recognizes the token and finds a value for it.   
```python
request = youtube.activities().list(
                part="snippet,contentDetails",
                mine=True
        )
```   
  
  
```python
#code you want.
for item in respones["items"]:
    print(item["snippet"]["channelId"])
```  
  
# [Read Before Use](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#:~:text=This%20is%20the%20prep%20code%20before%20writing%20the%20activity%2Drelated%20API.)  
>OAuth not enabled  
```python
#code you want.
for item in respones["items"]:
    print(item["snippet"]["publishedAt"])
```  


>OAuth enabled(Link with my account)  
>"mine=True"If this happens, instead of entering the channel ID, it recognizes the token and finds a value for it.   
```python
request = youtube.activities().list(
                part="snippet,contentDetails",
                mine=True
        )
```   
  
  
```python
#code you want.
for item in respones["items"]:
    print(item["snippet"]["publishedAt"])
```  
  
# [Read Before Use](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#:~:text=This%20is%20the%20prep%20code%20before%20writing%20the%20activity%2Drelated%20API.)  
>OAuth not enabled  
```python
#code you want.
for item in respones["items"]:
    print(item["snippet"]["title"])   
```  


>OAuth enabled(Link with my account)  
>"mine=True"If this happens, instead of entering the channel ID, it recognizes the token and finds a value for it.   
```python
request = youtube.activities().list(
                part="snippet,contentDetails",
                mine=True
        )
```   
  
  
```python
#code you want.
for item in respones["items"]:
    print(item["snippet"]["title"])   
```  
  
  
 # [Read Before Use](https://github.com/RCEcom/Youtube_API_Guide/blob/main/README.md#:~:text=This%20is%20the%20prep%20code%20before%20writing%20the%20activity%2Drelated%20API.)  
>OAuth not enabled  
```python
#code you want.
for item in respones["items"]:
    try:
        print("="*100)
        print("<default scale>")
        print("URL : {}".format(item["snippet"]["thumbnails"]["default"]["url"]))
        print("jpg width : {}, height : {}".format(item["snippet"]["thumbnails"]["default"]["width"],
                                                   item["snippet"]["thumbnails"]["default"]["height"]))
        print("<medium scale>")
        print("URL : {}".format(item["snippet"]["thumbnails"]["default"]["url"]))
        print("jpg width : {}, height : {}".format(item["snippet"]["thumbnails"]["medium"]["width"],
                                                   item["snippet"]["thumbnails"]["medium"]["height"]))
        print("<high scale>")
        print("URL : {}".format(item["snippet"]["thumbnails"]["default"]["url"]))
        print("jpg width : {}, height : {}".format(item["snippet"]["thumbnails"]["high"]["width"],
                                                   item["snippet"]["thumbnails"]["high"]["height"]))
        print("<standard scale>")
        print("URL : {}".format(item["snippet"]["thumbnails"]["default"]["url"]))
        print("jpg width : {}, height : {}".format(item["snippet"]["thumbnails"]["standard"]["width"],
                                                   item["snippet"]["thumbnails"]["standard"]["height"]))
        print("<maxres scale>")
        print("URL : {}".format(item["snippet"]["thumbnails"]["maxres"]["url"]))
        print("jpg width : {}, height : {}".format(item["snippet"]["thumbnails"]["maxres"]["width"],
                                                   item["snippet"]["thumbnails"]["maxres"]["height"]))
    except KeyError:
        break
```  


>OAuth enabled(Link with my account)  
>"mine=True"If this happens, instead of entering the channel ID, it recognizes the token and finds a value for it.   
```python
request = youtube.activities().list(
                part="snippet,contentDetails",
                mine=True
        )
```   
  
  
```python
#code you want.
for item in respones["items"]:
    try:
        print("="*100)
        print("<default scale>")
        print("URL : {}".format(item["snippet"]["thumbnails"]["default"]["url"]))
        print("jpg width : {}, height : {}".format(item["snippet"]["thumbnails"]["default"]["width"],
                                                   item["snippet"]["thumbnails"]["default"]["height"]))
        print("<medium scale>")
        print("URL : {}".format(item["snippet"]["thumbnails"]["default"]["url"]))
        print("jpg width : {}, height : {}".format(item["snippet"]["thumbnails"]["medium"]["width"],
                                                   item["snippet"]["thumbnails"]["medium"]["height"]))
        print("<high scale>")
        print("URL : {}".format(item["snippet"]["thumbnails"]["default"]["url"]))
        print("jpg width : {}, height : {}".format(item["snippet"]["thumbnails"]["high"]["width"],
                                                   item["snippet"]["thumbnails"]["high"]["height"]))
        print("<standard scale>")
        print("URL : {}".format(item["snippet"]["thumbnails"]["default"]["url"]))
        print("jpg width : {}, height : {}".format(item["snippet"]["thumbnails"]["standard"]["width"],
                                                   item["snippet"]["thumbnails"]["standard"]["height"]))
        print("<maxres scale>")
        print("URL : {}".format(item["snippet"]["thumbnails"]["maxres"]["url"]))
        print("jpg width : {}, height : {}".format(item["snippet"]["thumbnails"]["maxres"]["width"],
                                                   item["snippet"]["thumbnails"]["maxres"]["height"]))
    except KeyError:
        break
```  
  


