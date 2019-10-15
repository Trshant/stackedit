---
title: "Building a scaffolding for react using Docker"  
date: 2019-09-02T00:01:43+05:30  
draft: false  
tags : [ SoftareEngineering , WebDevelopment  , ReactJS , JavaScript , JavaScriptFramework , Docker  ]  
Description : "A note on using Docker to build a scaffolding to develop react apps and then using Docker to develop react apps"  
---

I used this set of files to setup and learn react while avoiding installing node or npm on my system. I do that to keep my system as new as the day it was installed - its a personal choice and while reports say that performance has deteriorated, it has not affected my productivity.

Lets start with the files.

The `docker-compose.yml`  I used
```docker-compose
version: '3'
	services:
		create_env:
			image: "create_env"
			build:
				context: .
			volumes:
				- ./code:/code
		<project_name>:
			build:
				context: .
				dockerfile: reactlearnDockerfile
			ports:
				- 3000:3000
			volumes:
				- ./code:/code
```

The `reactlearnDockerfile` file:
```dockerfile
FROM node:12.10.0-alpine  
RUN mkdir -p /code  
ADD ./code/ /code  
WORKDIR /code/<project_name>  
RUN npm install -g -s --no-progress yarn  
CMD ["yarn", "start"]  
EXPOSE 3000
```
The `Dockerfile` used. This is the default name and is used to build the image to setup the react scaffolding.
```dockerfile
FROM node:12.10.0-alpine  
RUN npm install -g create-react-app \  
                   create-react-native-app \  
                   react-native-cli  
RUN mkdir /code  
WORKDIR /code  
ADD . /code  
```

Save these files into a folder and `CD` into it. then change all occurances of ´\<project-name\>´ to ´learn-react´.

Alternatively, you can use this [gist](https://gist.github.com/Trshant/2cc6cf99749c979b8a1be5e39b45f757) and do this:
```sh
git clone https://gist.github.com/Trshant/2cc6cf99749c979b8a1be5e39b45f757 reactDir
cd reactDir
sed -i "s/\<project_name\>/learn-react" *
```
I am assuming you have sed installed and use ´learn-react´ as the project name you want to use.

Then build the `create_env` image
```sh
Docker-compose build react_env
```

use this built image to create the scaffolding for you
```sh
docker-compose run create_env create-react-app learn-react
```

Now you can use this scaffolding to develop your app:
```sh
docker-compose up learn-react --build
```



> Written with [StackEdit](https://stackedit.io/) and [VIM](https://www.vim.org/).
