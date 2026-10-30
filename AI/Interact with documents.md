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
set chunk size to 256 and overlap to 15%

## Create Knowledge base
Go to Workspace/Knowledge and Create
Then upload files

## Create Model
Go to Workspace/Models and Create
Then pick Base Model and pick Knowledge base

## Test which model can run 
granite4.1:3b    -> crash VM and host
llama3.2:latest -> is very slow
![[Pasted image 20261028234014.png]]
