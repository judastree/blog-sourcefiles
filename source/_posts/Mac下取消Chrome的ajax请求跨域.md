title: "Mac下取消Chrome/QQ浏览器的ajax请求跨域"
date: 2015-06-29 17:33:36
tags: [mac, 工具]
---

本地调试的时候总是说Origin * is not allowed by Access-Control-Allow-Origin好烦。

打开终端，输入命令

	$open -a "Google Chrome" --args --disable-web-security


用其他Chromium内核的浏览器的话，这个命令可能会不适用，比如我现在钟爱的QQ浏览器。

这时可以选择安装chrome extension的方式。CORS插件。

地址在这儿：[Allow-Control-Allow-Origin Extension](https://chrome.google.com/webstore/detail/allow-control-allow-origi/nlfbmbojpeacfghkpbjhddihlkkiljbi?utm_campaign=en&utm_source=en-et-na-us-oc-webstrhm&utm_medium=et)

