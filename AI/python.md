# Sources 
SiliconDojo
https://youtu.be/LJWMhmo-fAE?si=2wNl2UMJDTOpZKfR


# Requests
```bash
python3 -m venv sd
```

```bash
pip install requests
```

### request
```python
import requests
import json

url = 'http://ip-api.com/json/'

try:
    response = requests.get(url).json()

    print('='*30)
    print(response)

    print('='*30)
    print(f'You Are In This City: {response['city']}')

    print('='*30)
    for key, value in response.items():
        print(f'{key} -- {value}')

    print('='*30)
    print(json.dumps(response, indent=2))

    print('='*30)
except Exception as e:
    print(e)
except:
    print('There was an error')
else:
    print('ELSE runs when the TRY works')
finally:
    print('FINALLY always runs')
```
### Hello
```bash
class Message():
    alert = 'hello world'
    def hello(name):
        print(f'Hello {name}')
    def bye(name):
        print('Bye')

class Person:
    def __init__(self, name, age, size):
        self.name = name
        self.age = age
        self.size = size

student = Person('bob',11,'large')

person = 'bob'
Message.hello(person)
print(Message.alert)

print(student)
print(vars(student))
print(student.name)
print(student.age)
print(student.size)
```

### ping
```bash
import os

host = ['demotywatory.pl', 'amazon.pl']

command = 'ping -c 1 '

while True:
    print("check started...")
    page = '''
            <meta http-equiv="refresh" content="5">
            <h1>Up/Down Dashboard</h1>
            '''
    for site in host:
        print(f"checking {site}")
        response = os.popen(f'{command} {site}').read()
        page += f'<pre>{response}</pre>'

    with open('dashboard.html', 'w') as file:
        print(f"saved..")
        file.write(page)


```
###  joke
```bash
import requests

url = "https://official-joke-api.appspot.com/random_joke"

response = requests.get(url).json()

print(response['setup'])
print(response['punchline'])

with open('joke.html', 'w') as file:
	file.write('<h1>Joke Web App</h1>')
	file.write(f'<p>{response['setup']}</p>')
	file.write(f'</hr>')
	file.write(f'<p>{response['punchline']}</p>')
``` 

```text
What did the traffic light say to the car as it passed?
Don't look I'm changing!
```

### ollama_scirpt
```python
from ollama import chat, ChatResponse
import os
import requests

def geo():
    url = 'http://ip-api.com/json/'
    response = requests.get(url).json()

    return response

def ai(query, locationi, memroy):
    injection = 'Answer in under 20 words'
    query = f'''Follow these instructons: {injection}
                I am located here: {location}
                This is our conversation up until now: {memory}
                This is my question: {query}'''
    response: ChatResponse = chat(model='llama3.2', messages=[
        {
            'role': 'user',
            'content': query,
        },
    ])
    return response.message.content

location = geo()
with open('memory.txt', 'w') as file:
    file.write('This is the conversation we have had\n\n')
while True:
    query = input('Query: ')
    with open('memory.txt', 'r') as file:
        memory = file.read()
    response = ai(query, location, memory)
    os.system('clear')
    print(query)
    print(response)
    with open('memory.txt', 'a') as file:
        file.write(f'My Query: {query}\n')
        file.write(f'your Response: {response}\n\n')
```

### BeautifulSoup
```python
from ollama import chat, ChatResponse
from bs4 import BeautifulSoup
import requests

def scrape(url):
    page = requests.get(url).text
    soup = BeautifulSoup(page, "html.parser")
    paragraphs = soup.find_all("p")
    page_text = ''
    for line in paragraphs:
        page_text += line.text

    return page_text

def post(query):
    response: ChatResponse = chat(model='llama3.2', messages=[
        {
            'role': 'user',
            'content': query,
        },
    ])

    return response.message.content

def title(post):
    query = f'Create a 10 word Title for this post: {post}'
    response: ChatResponse = chat(model='llama3.2', messages=[
        {
            'role': 'user',
            'content': query,
        },
    ])

    return response.message.content

while True:
    url = input('URL: ')
    print("scrape faze...")
    text = scrape(url)
    query = f'''
            Write a 200 word blog post about this text: {text}
            '''
    print("post faze...")
    response_post = post(query)
    print("title faze...")
    response_title = title(text)

    print(response_title)
    print(response_post)
    print('*****')
    with open('autolog.html', 'a') as file:
        file.write(f'<h1>{response_title}</h1>')
        file.write(f'<p>{response_post}</p>')

```

### check arp
```bash
sudo apt install net-tools
```

```bash
from ollama import chat, ChatResponse
import os

def ai(query, network):
    query = f'''Based on this infromation from an apr -a command - {network}
                What is the answer to this question: {query}'''
    response: ChatResponse = chat(model='llama3.2', messages=[
        {
            'role': 'user',
            'content': query,
        },
    ])
    return response.message.content

network = os.popen('arp -a').read()

print(network)
while True:
    print("="*30)
    query = input('Question: ')
    response = ai(query, network)
    print(query)
    print(response)
```

### check pings
```python
from ollama import chat, ChatResponse
import os

def ai(query, network):
    query = f'''Based on this informaiton from a ping command - {network}
                What is the answer to this question: {query}
                Answer provide under 50 words'''
    response: ChatResponse = chat(model='llama3.2', messages=[
        {
            'role': 'user',
            'content': query,
        },
    ])
    return response.message.content

host = ['demotywatory.pl', 'onet.pl', 'wp.pl']

network = ''
for site in host:
    response = os.popen(f'ping -c 1 {site}').read()
    network+=response

print("+"*70)
print(network)
print("+"*70)
while  True:
    query = input('Question: ')
    response = ai(query, network)
    print("="*70)
    print(query)
    print(response)

```

```bash
python3 pingAI.py
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
PING demotywatory.pl (104.26.14.85) 56(84) bytes of data.
64 bytes from 104.26.14.85: icmp_seq=1 ttl=55 time=19.4 ms

--- demotywatory.pl ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 19.369/19.369/19.369/0.000 ms
PING onet.pl (13.227.146.66) 56(84) bytes of data.
64 bytes from server-13-227-146-66.waw51.r.cloudfront.net (13.227.146.66): icmp_seq=1 ttl=245 time=18.3 ms

--- onet.pl ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 18.296/18.296/18.296/0.000 ms
PING wp.pl (212.77.98.9) 56(84) bytes of data.
64 bytes from www.wp.pl (212.77.98.9): icmp_seq=1 ttl=56 time=15.0 ms

--- wp.pl ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 14.968/14.968/14.968/0.000 ms

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Question: Which is the fastest?
======================================================================
Which is the fastest?
The fastest ping result belongs to wp.pl with a time of 15.0 ms, followed by onet.pl with a time of 18.3 ms and demotywatory.pl with a time of 19.4 ms.
Question: 
```


# SQL
```bash
sudo apt install sqlite3
```

```sqlite
.help
```
```sqlite
.exit
```

```bash
sqlite3 class.db
```
