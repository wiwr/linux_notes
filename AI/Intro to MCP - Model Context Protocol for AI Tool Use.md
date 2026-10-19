notes for https://www.youtube.com/watch?v=TXrZ0ymjbZs

I will try to do that on VM with limited resources 
# VM
CPU 4
Memory 8192
Space 100
no GPU


## Preparation
```bash
ollama pull granite4.1:3b
```
alternative for 32GB of RAM
```bash
ollama pull gemma4:31b
```

```bash
python3 -m venv venv
```

```bash
source venv/bin/activate
```

```bash
python3 -m pip install ollama
```

```bash
python3 -m pip install mcp
```

mcp-client.py
```python
import asyncio
import ollama
import subprocess
from mcp import ClientSession, StdioServerParameters
from mcp.client.stdio import stdio_client
```
