# Source for notes
https://youtu.be/GWB9ApTPTv4?si=LDngtdshQ7SGEr5l


# VM
CPU 4
Memory 8192
Space 100
no GPU
## Snapshots
First after installation

# Post installation
```bash
sudo apt update && sudo apt upgrade -y
```

```bash
sudo apt install vim python3 
```

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

# Ollama
## llama3.2
```bash
ollama run llama3.2
```

```bash
ollama list
```

```bash
ollama rm llama3.2
```
## llava:7b
```bash
ollama run llava:7b
```

```txt
>>> what is this image ./flower_1.jpg
```
```txt
>>> and now write me a short poem about that
 A sunflower stands tall and proud,
with petals vibrant yellow and brown,
It faces towards the sky, like a compass for the day,
A symbol of joy, on a cloudy day.

Its head is full of seeds, for another plant to grow,
A life cycle repeating, in the ebb and flow.
The sunflower blooms with grace and style,
While we pass by, with a smile.

So let this sunflower be, a reminder of the day,
To appreciate life and what it has to say. 

```
### codellama

# Modelfile
```modelfile
FROM llama3.2

# set the temperature to 1 [higher is more createive, PARAMETER temperature 1, from 0 to 1]
PARAMETER temperature 0.3

SYSTEM """
        You are James, a very smart assistant who answers questions succintly and informatively.

"""
```

```bash
ollama create james -f ./Modelfile
```

```bash
ollama run james
```

```bash
>>> what is your name?
```

```bash
ollama rm james
```
# API
### Documentation
```bash
github.com/ollama/ollama/blob/main/docs/api.md
```

as stream
```bash
curl http://localhost:11434/api/generate -d '{"model": "llama3.2", "prompt":"Why is the sky blue?"}'
```
without stream
```bash
curl http://localhost:11434/api/generate -d '{"model":"llama3.2","prompt":"Why is the sky blue?", "stream":false}'
```

### Chat endpoint
```bash
curl http://localhost:11434/api/chat -d '{"model":"llama3.2", "messages": [{"role":"user", "content": "tell me a fun fact about Mozambique"}],"stream":false}'
```
### request json
```bash
curl http://localhost:11434/api/generate -d '{"model":"llama3.2","prompt":"What color is the sky at different times of the day? Respond using JSON", "format": "json", "stream":false}'
```
# Commands
`/bye` - to exit
`/clear` - to clear session
`/show info` - to get information about model
# Tips
can be added `in short`
`can you please be less verbose`
# Example prompt
```bash
>>> how to write prompt for you?
To write a prompt for me, consider the following tips:

1. **Be clear and concise**: Clearly state what you want to know or 
accomplish. Avoid vague or open-ended questions.
2. **Use specific language**: Use specific words and phrases that 
accurately describe your topic or question.
3. **Provide context**: Give me some background information or context 
about your question or topic, if applicable.
4. **Ask a specific question**: Ask a specific question or request a response to a particular prompt.

Here are some examples of good prompts:

* "Write a short story about a character who discovers a hidden world."
* "Explain the concept of artificial intelligence in simple terms."
* "Generate a list of 5 potential names for a new business startup."
* "Summarize the main points of the article 'The Impact of Climate Change on Global Food Systems'."
* "Create a conversation between two historical figures."

On the other hand, here are some examples of poor prompts:

* "Tell me something interesting."
* "What's the meaning of life?"
* "Write a poem about my feelings."
* "Explain everything about quantum mechanics in one sentence."

Avoid using phrases like "Just answer this" or "Make it true," as they can be too broad or ambiguous. Instead, try to provide more context and specificity.

If you're still unsure, feel free to ask me for clarification or help with your prompt!


```

# Models
https://ollama.com/search

### Useful commands
```bash
ssh user@ip
```

```bash
scp flower_1.jpg user@ip:/home/user
```

# Msty

[[https://msty.ai]]

Download
Install
Launch

# Python
```bash
sudo apt install python3-pip
```

```bash
sudo apt install python3.12-venv
```

```bash
python3 -m venv venv
```

```bash
source venv/bin/activate
```

```bash
pip install requests
```

```python
import requests
import json

url = "http://localhost:11434/api/generate"

data = {
        "model": "llama3.2",
        "prompt": "tell me a short story and make it funny"
}


response = requests.post(url, json=data, stream=True)

# check the response status
if response.status_code == 200:
    print("Generated Text:", end=" ", flush=True)
    # Iterate over the streaming response
    for line in response.iter_lines():
        if line:
            # Decode the line and parse the JSON
            decoded_line = line.decode("utf-8")
            result = json.loads(decoded_line)
            # Get the text from the response
            generated_text = result.get("response", "")
            print(generated_text, end="", flush=True)
else:
    print("Error:", response.status_code, response.text)
```

```bash
pyton3 start-1.py
```

### Ollama module
```bash
pip install ollama
```

```python
import ollama

response = ollama.list()

#print(response)
res = ollama.chat(
    model="llama3.2",
    messages=[
        {"role": "user", "content": "why is the sky blue?"},
    ],
)
print(res["message"]["content"])
```

```python
import ollama

response = ollama.list()

#print(response)
res = ollama.chat(
    model="llama3.2",
    messages=[
        {"role": "user", "content": "why is the sky blue?"},
    ],
    stream=True,
)
for chunk in res:
    print(chunk["message"]["content"], end="", flush=True)
```

```bash
python3 start-2.py
```

```python
import ollama

modelfile = """
FROM llama3.2
PARAMETER temperature 0.1
"""

ollama.create(model="knowitall",
              from_="llama3.2",
              system="You are very smart assistant who knows everything about oceans.",
              parameters={"temperatura": 0.1})
res = ollama.generate(model="knowitall", prompt="why is the ocean so solty")
print(res["response"])
```

```bash
python3 create.py
```

