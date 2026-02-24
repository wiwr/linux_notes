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

url = 'http://ip-api.com/json/'

response = requests.get(url).json()
print(response)
```
