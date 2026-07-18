Orchestration system. 

# Docker

## Examples
# First
package.json
```json
{
	"name": "simple-node",
	"version": "1.0.0",
	"description": "Example of application for Kubernetes book",
	"main": "server.js",
	"scripts": {
		"start": "node server.js"
	},
	"author": ""
}
```
server.js
```js
var express = require('express');
var app = express();
app.get('/', function (req, req) {
	res.send('Hello world');
});
app.listen(3000, function () {
	console.log('Listening on port 3000!');
	console.log('http://localhost:3000');
});
```

```bash
npm install express --save
```
.dockeringore
```Dockerfile
node_modules
```
Dockerfile
```Dockerfile
FROM node:10
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
CMD ["npm", "start"]
```

```bash
docker build -t simple-node .
```
```bash
docker run --rm -p 3000:3000 simple-node
```
