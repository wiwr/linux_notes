# Sources 
SiliconDojo

# Requests
```bash
python3 -m venv sd
```

```bash
pip install requests
```

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

