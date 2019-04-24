---
title: "Getting a LAMP dev setup using docker"
date: 2019-04-25T00:01:43+05:30
draft: true
tags : [programming , softwareEngineering , docker , LAMP ]
Description : "A note on how I started using Docker for LAMP development"
---
Following [A note on docker](https://trshant.dev/2019/01/27/A-note-on-docker.html), I decided to get a LAMP setup up using the only docker. However, I procrastinated for almost 3 months before the urge became too much to fight and I gave in and wanted to fight the good fight :stuck_out_tongue: 
Anyway, this post took almost 5 days to get done. so let us get to it.

First, I downloaded Docker and Docker-compose. I followed the official setup and finally got everything working. Docker-compose took a day to get installed properly, but it was mostly a badly installed python distribution that was causing the issue.  
  
  Once that was done, I created a folder and put in 2 files in it. Dockerfile and docker-compose.yml. it is linked in the link to the gist and you will be done. However, coming up with the exact file took a fair bit of time - in my case, almost 3 days.  
  
  A friend told me that I should use the base images given in the docker hub and work on those to get what I want. So I made the [Dockerfile]([https://gist.github.com/Trshant/e06bebd178915a7a025339c4bd5e5d94#file-dockerfile](https://gist.github.com/Trshant/e06bebd178915a7a025339c4bd5e5d94#file-dockerfile)) to get a base PHP/Apache image and wrote the remaining parts to install all the other extensions, so I would get a fully fledged system I could use anytime.  
    
  Post that I read up on Docker-compose and realized I better get started with writing a YAML file to detail out all the details. This has been carefully [commented](https://gist.github.com/Trshant/e06bebd178915a7a025339c4bd5e5d94#file-docker-compose-yml)) and I hope that the comments are good enough explanation.  
  
  Then all I needed to do was go over to that directory and do a `sudo docker-compose build` and post that `sudo docker-compose up`.
  
  Cheers! :beers:
 
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcyMjY3NTQxOV19
-->