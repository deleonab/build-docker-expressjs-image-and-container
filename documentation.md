
create Dockerfile

```
$ touch Dockerfile
```
create package.json file

```

$ touch package.json
```
 package.json content
 ```
{
    "dependencies": {
	"express": "^4.16.1"
    
}
}
 ```

 Create server.js
 ````

const express = require('express');

const app = express();

const HOST = '0.0.0.0';

const PORT = 80;

app.get('/', (req,res)=>{

    res.send('Hello World');

    app.listen(PORT, HOST);

    console.log(`Server is currently running on port ${PORT}`);




})
 ```
Dockerfile contents
```
FROM node
WORKDIR /app
COPY . . 
RUN npm install
CMD ["node","server.js"]
```