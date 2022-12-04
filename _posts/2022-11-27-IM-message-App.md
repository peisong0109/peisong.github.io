---
layout: post
read_time: true
show_date: true
title: "Design an IM App using wildfire"
date: 2022-11-27
img: posts/20221127/IM.png
tags: [IM]
category: Knowledge
author: Peisong Li
description: "Design an IM App using wildfire."
---
## Tutorial
[Tutorial of WildFire IM](https://docs.wildfirechat.cn/)

## Deployment of the server
### IM service
#### Step1: Download the source code
Download the latest version of release from:

https://github.com/wildfirechat/im-server

Here we download the latest version (tar), then unzip and copy it to the cloud server.

![image](./assets/img/posts/20221127/step1-1.png)

#### Step2: Start the service
Then, just follow the [tutorial](https://docs.wildfirechat.cn/quick_start/server.html).


### Demo application service
#### Step1: Download the source code
Download the latest version of release from:

https://github.com/wildfirechat/app-server

Here we download the latest version (tar), then unzip and copy it to the cloud server.

![image](./assets/img/posts/20221127/step2-1.png)

#### Step2: Start the service
Then, just follow the [tutorial](https://docs.wildfirechat.cn/quick_start/server.html).

## Deployment of the Android app
#### Step1:  Download the source code and run it with Android Studio
https://github.com/wildfirechat/android-chat

#### Step2: Modify the config file
  https://docs.wildfirechat.cn/quick_start/android.html

## Change the database
#### Change the database to MySQL:
```
sudo docker run -p 3307:3306 --name mysql  -e MYSQL_ROOT_PASSWORD=123456 -d mysql:latest
```

#### Modify the config file.

![image](./assets/img/posts/20221127/step3.png)



