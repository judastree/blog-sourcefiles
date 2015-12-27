title: "Android怎么打Log"
date: 2015-07-14 09:36:07
tags: [Android]
---

android 中有五种类型的 Log .

    VERBOSE 类型调试信息，verbose啰嗦的意思 
    DEBUG 类型调试信息, debug调试信息 
    INFO  类型调试信息, 一般提示性的消息information 
    WARN  类型调试信息，warning警告类型信息 
    ERROR 类型调试信息，错误信息
     
那么怎么在logcat中打印出这几种类型的日志呢。

Android.util.Log类提供如下对应的方法。
        
        Log.v(String tag, String msg); //VERBOSE 
        Log.d(String tag, String msg); //DEBUG 
        Log.i(String tag, String msg); //INFO 
        Log.w(String tag, String msg); //WARN 
        Log.e(String tag, String msg); //ERROR 
   
Tag为调试信息标签名称，msg为添加的调试信息 。

这样你可以根据tag，在DDMS中对不同类型的日志进行过滤查看。

但真正的项目中，我们会在 debug 的版本中输出 log，而在 release 版本的产品中关闭 log 的输出。

要控制日志的输出与否，我们仍需要自己根据当前环境去封装自己的Log类。

比如，在Release 版本的软件上将 DEBUG 置为 false ：

    public class Log {
     private static final boolean DEBUG = true;
       
     public static void v(String tag, String msg) {
         if(DEBUG) {
          android.util.Log.v(tag, msg);
         }
        }
        public static void v(String tag, String msg, Throwable tr) {
            if(DEBUG) {
             android.util.Log.v(tag, msg, tr);
            }
        }
        public static void d(String tag, String msg) {
            if(DEBUG) {
             android.util.Log.d(tag, msg);
            }
        }
        public static void d(String tag, String msg, Throwable tr) {
            if(DEBUG) {
             android.util.Log.d(tag, msg, tr);
            }
        }
        public static void i(String tag, String msg) {
            if(DEBUG) {
             android.util.Log.i(tag, msg);
            }
        }
        public static void i(String tag, String msg, Throwable tr) {
            if(DEBUG) {
             android.util.Log.i(tag, msg, tr);
            }
        }
        public static void w(String tag, String msg) {
            if(DEBUG) {
             android.util.Log.w(tag, msg);
            }
        }
        public static void w(String tag, String msg, Throwable tr) {
            if(DEBUG) {
             android.util.Log.w(tag, msg, tr);
            }
        }
        public static void w(String tag, Throwable tr) {
            if(DEBUG) {
             android.util.Log.w(tag, tr);
            }
        }
        public static void e(String tag, String msg) {
            if(DEBUG) {
             android.util.Log.e(tag, msg);
            }
        }
        public static void e(String tag, String msg, Throwable tr) {
            if(DEBUG) {
             android.util.Log.e(tag, msg, tr);
            }
        }
    }


        