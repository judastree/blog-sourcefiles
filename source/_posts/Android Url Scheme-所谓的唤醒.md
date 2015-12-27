title: "Android Url Scheme 所谓的唤醒"
date: 2015-07-14 10:47:58
tags: [Android]
---

所谓的唤醒，就是从浏览器端（或者微信等第三方的app）打开指定app的动作。

IOS上有Url scheme的概念，可以配置每个app的启动协议。就相当于用http的协议地址会默认打开Safari这个app一样。

那么在安卓app中如何设置呢？

只要在AndroidMainifest.xml中对你要启动的那个activity加入如下描述。

        <activity
            android:name="com.android.demo.MainActivity"
            android:label="@string/app_name" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
            <intent-filter android:priority="4000">
                <action android:name="android.intent.action.VIEW"/>
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
                <data
                    android:host="homepae"
                    android:scheme="myapp" />
            </intent-filter>

        </activity>

那么当我在浏览器中访问如 "myapp://homepage"这个协议地址时，它就会唤醒com.android.demo.MainActivity这个客户端的页面。
