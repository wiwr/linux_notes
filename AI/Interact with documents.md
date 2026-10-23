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