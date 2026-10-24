# VM
CPU 4
Memory 8192
Space 100
no GPU

# Preparation

```bash
sudo apt update && sudo apt upgrade -y
```

```bash
sudo apt install vim python3 
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
ollama list
```

```bash
pip install open-webui
```

```bash
open-webui serve
```

```bash
http://<ServerIP>:8080
```
```bash
http://192.168.122.58:8080
```

Then create admin account

```bash
ollama pull nomic-embed-text
```

Check how to add memory to ai
Go to Settings / Personalization / Memory
Go to Admin Panel / Settings / Documents / Embedding Model Engine and set to Ollama
in Embedding Model put nomic-embed- text
then Retrival enable "Full Context Mode"