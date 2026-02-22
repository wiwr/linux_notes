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
## Environment 
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

## Simple requests
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

```python
import ollama
import os

model = "llama3.2"

input_file = "./data/grocery_list.txt"
output_file = "./data/categorized_grocery_list.txt"

if not os.path.exists(input_file):
    print(f"Input file '{input_file}' not found.")
    exit(1)

with open(input_file, "r") as f:
    items = f.read().strip()

prompt = f"""
You are an assistant that categorizes and sorts grocery items.

Here is a list of grocery items:

{items}

Please:

1. Categorize these items into appropriate categorizes such as Produce, Dairy, Meat, Bakery, Beverages, etc.
2. Sort the items alphabetically within each category.
3. Present the categorized list in a clear and organized manner, using bullet points or numbering.
"""

try:
    response = ollama.generate(model=model, prompt=prompt)
    generated_text = response.get("response", "")
    print("===== Categorized List: =======\n")
    print(generated_text)

    with open(output_file, "w") as f:
        f.write(generated_text.strip())

    print(f"Categorized grocery list has been saved to '{output_file}'.")
except Exception as e:
    print("An error occurred:", str(e))

```

```bash
python3 categorizer.py
```

# RAG
Create data source
```txt
ollama>=0.1.0
chromadb==0.5.23
pdfplumber==0.10.0
langchain==1.2.10
langchain-core
langchain-ollama==1.0.1
langchain-community==0.4.1
langchain-text-splitters==1.1.1
unstructured
unstructured[all-docs]==0.8.3
sentence-transformers==2.2.2
opencv-python-headless>=4.13.0.90
elevenlabs==2.36.1
```

```bash
pip install -r requirements.txt
```

```bash
pip uninstall opencv-python
```

```bash
pip install opencv-python-headless
```

```bash
pip uninstall -y langchain langchain-core langchain-community langchain-classic langchain-ollama langchain-text-splitters
```

```bash
ollama pull nomic-embed-text
```

```bash
ollama pull llama3.2
```

```python
from langchain_community.document_loaders import UnstructuredPDFLoader
from langchain_community.document_loaders import OnlinePDFLoader

doc_path = "./data/boi.pdf"
model = "llama3.2"

if doc_path:
	loader = UnstructuredPDFLoader(file_path=doc_path)
	data = loader.load()
	print("done loading...")
else:
	print("Upload a PDF file")
	
content = data[0].page_content
#print(content[:100])

from langchain_ollama import OllamaEmbeddings
from langchain_text_splitters import RecursiveCharacterTextSplitter
from langchain_community.vectorstores import Chroma

text_splitter = RecursiveCharacterTextSplitter(chunk_size=1200, chunk_overlap=300)
chunks = text_splitter.split_documents(data)
print("done splitting...")

#print(f"Number of chunks: {len(chunks)}")
#print(f"Example chunk: {chunks[0]}")

import ollama
ollama.pull("nomic-embed-text")

vector_db = Chroma.from_documents(
	documents=chunks,
	embedding=OllamaEmbeddings(model="nomic-embed-text"),
	collection_name="simple-rag",
	persist_directory="./chroma_db",
)
print("done adding to vector database...")

from langchain_core.prompts import ChatPromptTemplate, PromptTemplate
from langchain_core.output_parsers import StrOutputParser

from langchain_ollama import ChatOllama

from langchain_core.runnables import RunnablePassthrough
from langchain.retrievers.multi_query import MultiQueryRetriever

llm = ChatOllama(model=model)

QUERY_PROMPT = PromptTemplate(
	input_variables=["question"],
	template="""You are an AI Language model assistant. Your task is to generate five different versions of the given user question to retrieve document from a vector database. By generating multiple perspectives on the user question, your goal is to help the user overcome some of the limitations of the distance-based similarity search. Provide these alternative questions separated by newlines. Original question: {question}""",
)

retriever = MultiQueryRetriever.from_llm(
	vector_db.as_retriever(), llm, prompt=QUERY_PROMPT
)

template = """Answer the question based ONLY on the following context:
{context}
Question: {question}
"""
prompt = ChatPromptTemplate.from_template(template)
chain = (
	{"context": retriever, "question": RunnablePassthrough()}
	| prompt
	| llm
	| StrOutputParser()
)

res = chain.invoke({"question": "what is the document about?"})
# res = chain.invoke(
#	input=("what are the main points as a business owner I should be aware off?",)	
#	)
#res = chain.invoke(input=("how to report BOI?",))
print(res)
```