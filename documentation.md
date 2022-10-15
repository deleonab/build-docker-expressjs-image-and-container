
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

docker build -t dele/express
```
$ docker build . -t dele/express
Sending build context to Docker daemon  100.9kB
Step 1/5 : FROM node
 ---> 3adbe565b1f0     
Step 2/5 : WORKDIR /app
 ---> Running in bb5e96a4b054
Removing intermediate container bb5e96a4b054
 ---> 47ff2c90c0ae
Step 3/5 : COPY . .
 ---> 11c13c9fb63f
Step 4/5 : RUN npm install
 ---> Running in d648ea43cef9

added 57 packages, and audited 58 packages in 4s

7 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
npm notice
npm notice New minor version of npm available! 8.15.0 -> 8.19.2
npm notice Changelog: <https://github.com/npm/cli/releases/tag/v8.19.2>
npm notice Run `npm install -g npm@8.19.2` to update!
npm notice
Removing intermediate container d648ea43cef9
 ---> 17aa31c0f63e
Step 5/5 : CMD ["node","server.js"]
 ---> Running in 9cb88c4b8148
Removing intermediate container 9cb88c4b8148
 ---> 0491f011dd77
Successfully built 0491f011dd77
Successfully tagged dele/express:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.

```