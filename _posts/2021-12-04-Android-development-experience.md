---
layout: post
read_time: true
show_date: true
title: "Common-used library in my Android project"
date: 2021-12-04
img: posts/20211204/Android.jpg
tags: [android]
category: experience
author: Peisong Li
description: "Common-used library in my Android project, like data transmission, thread and lifecycle management."
---

### The records of the development of the Android app

## Thread

### Eventbus
 [EventBus](https://github.com/greenrobot/EventBus)
Step1:
Start a new class, here defines the message type and content:

    public class MessageEvent {  
      
        private String message;  
        private int type;  
      
        public MessageEvent(int type, String message) {  
            this.type = type;  
            this.message = message;  
        }  
      
        public String getMessage() {  
            return message;  
        }  
      
        public void setMessage(String message) {  
            this.message = message;  
        }  
      
        public int getType() {  
            return type;  
        }  
      
        public void setType(int type) {  
            this.type = type;  
        }   }
Step2:
In BaseActivity, register and unregister the EventBus:

        @Override  
      protected void onCreate(Bundle savedInstanceState){  
            super.onCreate(savedInstanceState);  
        
      EventBus.getDefault().register(this);  
    }
    @Override  
    protected void onRestart() {  
        super.onRestart();  
        if (!EventBus.getDefault().isRegistered(this)){  
            EventBus.getDefault().register(this);  
            Log.d("BaseState","Event true");  
        }  
    }  
    @Override  
    protected void onDestroy() {  
        EventBus.getDefault().unregister(this);  
        Log.d("BaseState","Event false");  
        super.onDestroy();  
      
    }
Step3: Listener

    @Subscribe(threadMode = ThreadMode.MAIN)  
    public void onMessageEvent(MessageEvent event) {  
        switch (event.getType()){  
            case 0:  
                FancyToast.makeText(this,"Failed to upload. "+event.getMessage(),FancyToast.LENGTH_SHORT, FancyToast.ERROR,false).show();  
      
                break;  
            case 1:  
                FancyToast.makeText(this, event.getMessage(),FancyToast.LENGTH_SHORT, FancyToast.SUCCESS,false).show();  
                break;  
            case 2:  
                FancyToast.makeText(this, getString(R.string.toast_login), FancyToast.LENGTH_LONG, FancyToast.WARNING, false).show();  
                break;  
        }  
    };

## Toast
 [FancyToast](https://github.com/Shashank02051997/FancyToast-Android)

     FancyToast.makeText(this,"Failed to upload. "+event.getMessage(),FancyToast.LENGTH_SHORT, FancyToast.ERROR,false).show();

## Dialog
 [Dialogue](https://github.com/searchy2/CustomAlertViewDialogue)


## Data transmission
 [OKHTTP](https://github.com/square/okhttp)
 
Step1:

    implementation 'com.squareup.okhttp3:okhttp:4.9.0'
Step2: An example class which transmits audio to the backend server.

        public class AudioUploading {  
          
            private static final String IMGUR_CLIENT_ID = "123";  
            private static final MediaType MEDIA_TYPE_WAV = MediaType.parse("audio/wav");  
            private static final OkHttpClient client = new OkHttpClient();  
          
            public static void run(File f, String pro, String phone) throws Exception {  
                final File file=f;  
                new Thread() {  
                    @Override  
          public void run() {  
                        //Thread  
          RequestBody requestBody = new MultipartBody.Builder()  
                                .setType(MultipartBody.FORM)  
                                .addFormDataPart("pro", pro)  
                                .addFormDataPart("phone", phone)  
                                .addFormDataPart("file", file.getName(),  
                                        RequestBody.create(file, MEDIA_TYPE_WAV))  
                                .build();  
                        //Your IP  
          Request request = new Request.Builder()  
                                .header("Authorization", "Client-ID " + IMGUR_CLIENT_ID)  
                                .url("http://XXX.XXX.XX.XX:5000/upload")  
                                .post(requestBody)  
                                .build();  
                        try (Response response = client.newCall(request).execute()) {  
                            if (!response.isSuccessful()){  
                                EventBus.getDefault().post(new MessageEvent(0,"Unexpected code " + response));  
                            }  
        //                    if (!response.isSuccessful()) throw new IOException("Unexpected code " + response);  
          
        //                    System.out.println(response.body().string());  
          EventBus.getDefault().post(new MessageEvent(1,response.body().string()));  
                        } catch (IOException e) {  
                            e.printStackTrace();  
                        }  
                    }  
                }.start();  
            }  
        }

Step3: Call the method to upload the wav audio:

      private void uploadResult(String pro) {  
          String path = getExternalFilesDir(Environment.DIRECTORY_MUSIC) + "/test.wav";  
                boolean fileExist = fileIsExists(path);  
                if (fileExist) {  
          try {  
                        //Uploading the audio   
          AudioUploading.run(f, pro, phoneNum);  
                    } catch (Exception e) {  
                        e.printStackTrace();  
                    }  
                } 
            }
References:
 [Official tutorial](https://square.github.io/okhttp/recipes/)


## Loading
 [Progress](https://github.com/Kaopiz/KProgressHUD)


## BaseActivity
Example:

    public abstract class BaseActivity extends AppCompatActivity {  
        private KProgressHUD hud;  
      
        @Override  
      protected void onCreate(Bundle savedInstanceState){  
            super.onCreate(savedInstanceState);  
      
            //注册事件  
      EventBus.getDefault().register(this);  
      
    }  
        @Override  
      protected void onStart() {  
            Log.i(TAG, "onStart");  
      
            super.onStart();  
        }  
      
        @Subscribe(threadMode = ThreadMode.MAIN)  
        public void onMessageEvent(MessageEvent event) {  
            switch (event.getType()){  
                case 0:  
                    FancyToast.makeText(this,"Failed to upload. "+event.getMessage(),FancyToast.LENGTH_SHORT, FancyToast.ERROR,false).show();  
      
                    break;  
                case 1:  
                    FancyToast.makeText(this, event.getMessage(),FancyToast.LENGTH_SHORT, FancyToast.SUCCESS,false).show();  
                    break;  
                case 2:  
                    FancyToast.makeText(this, getString(R.string.toast_login), FancyToast.LENGTH_LONG, FancyToast.WARNING, false).show();  
                    break;  
                case 3:  
                    hud = KProgressHUD.create(this)  
                            .setStyle(KProgressHUD.Style.SPIN_INDETERMINATE)  
                            .setLabel(getString(R.string.hud_wait))  
                            .setDetailsLabel(getString(R.string.hud_prc))  
                            .setBackgroundColor(ContextCompat.getColor(this, R.color.teal_200))  
                            .show();  
                    break;  
                case 4:  
                    if (hud.isShowing()){  
                        hud.dismiss();  
                    }  
                    break;  
      
            }  
        };  
      
        @Override  
      protected void onRestart() {  
            super.onRestart();  
            if (!EventBus.getDefault().isRegistered(this)){  
                EventBus.getDefault().register(this);  
                Log.d("BaseState","Event true");  
            }  
        }  
      
        @Override  
      protected void onStop() {  
            super.onStop();  
      
        }  
        @Override  
      protected void onDestroy() {  
            EventBus.getDefault().unregister(this);  
            Log.d("BaseState","Event false");  
            super.onDestroy();  
      
        }  
      
    }

It usually includes the lifecycle of the activity, register and unregister of services and others. 

![Lifecycle](./assets/img/posts/20211204/Lifecycle.jpg)





