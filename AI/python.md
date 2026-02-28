# Sources 
SiliconDojo

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