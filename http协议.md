# HTTP协议 #

一.什么是HTTP协议
```
客户端连上web服务器后，若想获得web服务器中的某个web资源，需遵守一定的通讯格式，HTTP协议用于定义客户端与web服务器通迅的格式。

使用telnet程序连上web服务器，并使用HTTP协议获取某个页面，以快速了解 HTTP协议的作用。

利用一些浏览器的插件可以查看Http协议的详细内容（如IE的HttpWatch，火狐的firebug，Ghrome自带工具）。

```

二.HTTP协议简介
```
HTTP是hypertext transfer protocol（超文本传输协议）的简写，它是TCP/IP协议的一个应用层协议，用于定义WEB浏览器与WEB服务器之间交换数据的过程。

HTTP协议是学习JavaWEB开发的基石，不深入了解HTTP协议，就不能说掌握了WEB开发，更无法管理和维护一些复杂的WEB站点。

HTTP协议的版本：HTTP/1.0、HTTP/1.1
```
三.HTTP请求
```
客户端连上服务器后，向服务器请求某个web资源，称之为客户端向服务器发送了一个HTTP请求。一个完整的HTTP请求包括如下内容：
	一个请求行、若干请求头、以及实体内容，其中的一些消息头和实体内容都是可选的，消息头和实体内容之间要用空行隔开。如下所示 ：

GET /books/java.html HTTP/1.1------------->请求行（请求行用于描述客户端的请求方式、请求的资源名称，以及使用的HTTP协议版本号）
Accept: */*---------------------------------|
Accept-Language: en-us                      |
Connection: Keep-Alive                      |
Host: localhost                             | ---> 多个消息头(消息头用于描述客户端请求哪台主机，以及客户端的一些环境信息等)
Referer: http://localhost/links.asp         |           
User-Agent: Mozilla/4.0                     |
Accept-Encoding: gzip, deflate--------------|
------------------------------------------------>一个空行
```
四.HTTP请求的细节——请求行
```
请求行中的GET称之为请求方式，请求方式有：
	POST、GET、HEAD、OPTIONS、DELETE、TRACE、PUT
	常用的有：POST、GET
不管POST或GET，都用于向服务器请求某个WEB资源，这两种方式的区别主要表现在数据传递上，客户端通过这两种方式都可以带一些数据给服务器：
如请求方式为GET方式，则可以在请求的URL地址后以?的形式带上交给服务器的数据，多个数据之间以&进行分隔，例如：
		GET /mail/1.html?name=abc&password=xyz HTTP/1.1
		GET方式的特点：在URL地址后附带的参数是有限制的，其数据容量不能超过1K。
如请求方式为POST方式，则可以在请求的实体内容中向服务器发送数据，例如：
	POST /servlet/ParamsServlet HTTP/1.1
	Host:
	Content-Type: application/x-www-form-urlencoded
	Content-Length: 28
	name=abc&password=xyz
	Post方式的特点：传送的数据量无限制。
```
五.HTTP请求的细节——请求头
```
用于HTTP请求中的常用头
Accept: text/html,image/*
Accept-Charset: ISO-8859-1
Accept-Encoding: gzip,compress
Accept-Language: en-us,zh-
Host: www.baidu.com:80
If-Modified-Since: Tue, 11 Jul 2000 18:23:51 GMT
Referer: http://www.baidu.com/index.jsp   
User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows NT 5.0)
Cookie:
Connection: close/Keep-Alive
Date: Tue, 11 Jul 2000 18:23:51 GMT

```
