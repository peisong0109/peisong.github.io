---
layout: post
read_time: true
show_date: true
title: "Build a simple server based on the python Flask library"
date: 2021-12-04
img: posts/20211204/flask.jpg
tags: [server, python, Flask, OkHTTP]
category: Server
author: Peisong Li
description: "You can build and dockerize a python-based backend server in 5 minutes."
---

## Background:
In my project, I need to build a server for the mobile users. After a research, I found that the **python's Flask library** probably is a great framework. In addition, the server is built as a docker container, so it's easy for us to transfer.
For the mobile Android users, they need to upload the audio data to the server, so we implement the **OKHTTP** for the communication and data transmission between client and server.

## Dokcer:
First of all, you need to build a docker environment on your server, which is not the key point in this article.

## Server:
**Step1:**
Firstly, we start with creating a new directory:

    cd flask_server

Secondly, come into the forder and build the required files:

![File category](./assets/img/posts/20211204/Category.jpg)

Dockerfile:

    FROM python:3.8
    RUN pip install --upgrade pip
    WORKDIR /usr/src/app    
    
    COPY requirements.txt ./  
    RUN pip install --no-cache-dir -r requirements.txt
    
    COPY . .    
    
    CMD [ "python", "./Server.py" ]

requirements.txt:

    Flask==2.0.2

Server.py:

    # @Time    : 2021-12-01 11:54
    # @Author  : Peisong Li
    # @FileName: Server.py
    
        from flask import Flask, request
        import os
        from werkzeug.utils import secure_filename
        import time
        
        os.environ['TZ'] = 'Asia/Shanghai'
        time.tzset()
        app = Flask(__name__)
        
        @app.route('/')
        def hello_world():
            return 'Hi, this is a server running in a Docker container!'
        
        @app.route('/upload', methods=['POST', 'GET'])
        def upload():
            if request.method == 'POST':
                # Get the tags
                f = request.files['file']
                pro = request.form['pro']
                ph = request.form['phone']
                datatime = time.strftime('%Y-%m-%d_%H:%M:%S', time.localtime())
                # root path
                basepath = os.path.dirname(__file__)
                # The Audio folder must be created in advance.
                upload_path = os.path.join(basepath, 'Audio', pro+'-'+datatime+'-'+ph+'-'+secure_filename(f.filename))
                # Save the file
                f.save(upload_path)
                return 'Success.'
    
    if __name__ == '__main__':
        app.run(debug=True, host='0.0.0.0')

**Step2:**
Build the image:

    # docker build -t flask-server .
Here the image name is *flask-server*, you can name it your own.

**Step3:**
Run the container:

    # sudo docker run -it --name py-server -p 5000:5000 -v "$PWD":/usr/src/app flask-server


Now, the website XX.XX.XX.XX:5000 is available. (Replace XX.XX.XX.XX with you own IP.)
Also, you can upload the file from your client by this url: 
XX.XX.XX.XX:5000/upload
In the next chapter, I'll show how to send a file from the client to the server. Here we use OkHttp to do that.

## Client:
The Android client could upload the audio data or other files to the server. Here we show the process of uploading the .wav audio.

I just present the source code, I believe you can understand it. 
Just copy and take a try!

1. Build the method:

        public class AudioUploading {  
          
            private static final String IMGUR_CLIENT_ID = "123";  
            private static final MediaType MEDIA_TYPE_WAV = MediaType.parse("audio/wav");  
            private static final OkHttpClient client = new OkHttpClient();  
          
            public static void run(File f, String pro, String phone) throws Exception {  
                final File file=f;  
                new Thread() {  
                    @Override  
          public void run() {  
                        //Sub Thread
          RequestBody requestBody = new MultipartBody.Builder()  
                                .setType(MultipartBody.FORM)  
                                .addFormDataPart("pro", pro)  
                                .addFormDataPart("phone", phone)  
                                .addFormDataPart("file", file.getName(),  
                                        RequestBody.create(file, MEDIA_TYPE_WAV))  
                                .build();  
                        //your ip address  
          Request request = new Request.Builder()  
                                .header("Authorization", "Client-ID " + IMGUR_CLIENT_ID)  
                                .url("http://**.**.**.**:5000/upload")  
                                .post(requestBody)  
                                .build();  
                        try (Response response = client.newCall(request).execute()) {    
                            if (!response.isSuccessful()) throw new IOException("Unexpected code " + response);  
                            System.out.println(response.body().string());  
                        } catch (IOException e) {  
                            e.printStackTrace();  
                        }  
                    }  
                }.start();  
            }  
        }

2. Call the method:

    AudioUploading.run(f, pro, phoneNum);  

## Source code:
[The source code](https://github.com/peisong0109/python-server)

For more information, you can refer the official tutorial below.

 1. [Flask](https://flask.palletsprojects.com/en/2.0.x/quickstart/#http-methods)
    
 2. [OkHttp](https://square.github.io/okhttp/recipes/)


