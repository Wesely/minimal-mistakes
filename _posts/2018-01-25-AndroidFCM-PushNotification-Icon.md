---

title:  "Android FCM Push-Notification Icon"
header:
  teaser: "https://i.imgur.com/hXjp70z.png"
categories: 
  - Android
tags:
  - FCM
---

<a href="https://i.imgur.com/hXjp70z.png"><img src="https://i.imgur.com/hXjp70z.png"></a>
    
In Android FCM Push-Notification, you should design your icon with alpha layer.
    
The alpha layer is the first 2 digits of ARGB hex-color (0xAARRGGBB), which representing the transparency of a pixel.
Android system will extract the alpha value, makes RGB color useless here.

Example : 
<img src="https://i.imgur.com/kI7jqNy.png"/>

This image's alpha layer represents white-level on dark AppBar, 

<img src="https://i.imgur.com/hXjp70z.png"/>

and black-level on white AppBar,

<img src="https://i.imgur.com/ALboBzW.png"/>
    
## Implementing Customize Icon

**Info Notice:**
- Assume you've already implemented FCM and can recieve messages.
- In `app:gradle`, I'm using this version `implementation 'com.google.firebase:firebase-messaging:11.0.2'`
(FCM 11.8.0 is available but it's customize icon feature seems have some issue.)
{: .notice--info}


- In the `Service` extends `FirebaseMessagingService`. and @Override `onMessageReceived`:
``` java
public class MyFCMService extends FirebaseMessagingService {
    public MyFCMService() {
    }

    @Override
    public void onMessageReceived(RemoteMessage remoteMessage) {
        String title=remoteMessage.getNotification().getTitle();
        String message=remoteMessage.getNotification().getBody();
        Intent intent=new Intent("package.name.strings.FCM_LANDING");
        intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
        PendingIntent pendingIntent=PendingIntent.getActivity(this,0,intent,PendingIntent.FLAG_ONE_SHOT);
        NotificationCompat.Builder notificationBuilder=new NotificationCompat.Builder(this, "default_channel_id"); // default channels
        notificationBuilder.setContentTitle(title);
        notificationBuilder.setColor(0xFF0077CC);
        notificationBuilder.setContentText(message);
        notificationBuilder.setSmallIcon(R.mipmap.android_push_icon); 
	}
}
```

- Declare it in `manifests.xml`
  
```xml
<activity .....>
	...
    <meta-data
	android:name="com.google.firebase.messaging.default_notification_channel_id"
	android:value="default_channel_id"/>
    <!-- this icon declarition won't work in some SDK version-->
    <meta-data
	android:name="com.google.firebase.messaging.default_notification_icon"
	android:resource="@mipmap/android_push_icon" />
    <service android:name=".fcm.MyFCMService">
        <intent-filter>
    	<action android:name="com.google.firebase.MESSAGING_EVENT" />
        </intent-filter>
    </service>
<activity>
```
