notes for https://www.youtube.com/watch?v=TXrZ0ymjbZs
git repo of SiliconDojo for MCP https://github.com/SiliconDojo/In-Person-Classes/tree/main/MCP%20-%20Model%20Context%20Protocol
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

OLLAMA_MODEL = "granite4.1:3b"
MCP_SERVER = "mcp-server-system-health.py"

server_params = StdioServerParameters(
	command="pyton3",
	args=[MCP_SERVER],
)

def mcp_tools_to_ollama_format(mcp_tools):
	tools = []
	for t in mcp_tools:
		tools.append({
			"type": "function",
			"function": {
				"name": t.name,
				"description": t.description or "",
				"paramters": t.input_schema or {"type": "object", "properties": {}},
			},
		})
	return tools
	
async def query_ai(query):
	async with stdio_client(server_params) as (read, write):
		async with ClientSession(read, write) as session:
			await session.initialize()
			tools_result = await session.list_tools()
			ollama_tools = mcp_tools_to_ollama_format(tools_result.tools)
			
			messages = [
				{
					"role": "system",
					"content": "You are a helpful assistant with acess to local system tools adn automation. "
					"Use the provided tools to answer the user's request whenever necessary. "
					"Be brief"
				},
				{"role": "user", "content": query}
			]
			for _ in range(10):
				response = ollama.chat(
					model=OLLAMA_MODEL,
					messages=messages,
					tools=ollama_tools,
				)
				
				msg = response["message"]
				messages.append(msg)
				
				if msg.get("tool_calls"):
					for call in msg["tool_calls"]:
						name = call["function"]["name"]
						args = call["function"]["arguments"]
						
						result = await session.call_tool(name, arguments=args)
						tool_output = "".join(
							c.text for c in result.content if hasattr(c, "text")
						)
						messages.append({
							"role": "tool",
							"content": tool_output,
							"name": name,
						})
						
					final = ollama.chat(model=OLLAMA_MODEL, messages=messages)
					result = final["message"]["content"]
				else:
					result = msg["content"]
	return result
	
while True:
	query = input('Query About System: ')
	subprocess.run(['clear'])
	response = asyncio.run(query_ai(query))
	print(query)
	print(response)			
```
