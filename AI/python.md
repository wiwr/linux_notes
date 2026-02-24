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
