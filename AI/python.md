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

```
