# HttpServletRequest #
一.HttpServletRequest
```
HttpServletRequest对象代表客户端的请求，当客户端通过HTTP协议访问服务器时，HTTP请求头中的所有信息都封装在这个对象中，开发人员通过这个对象的方法，可以获得客户这些信息。
```
二.Request常用方法
```
获得客户机信息
getRequestURL方法返回客户端发出请求时的完整URL。
getRequestURI方法返回请求行中的资源名部分。
getQueryString 方法返回请求行中的参数部分。
getPathInfo方法返回请求URL中的额外路径信息。额外路径信息是请求URL中的位于Servlet的路径之后和查询参数之前的内容，它以“/”开头。
getRemoteAddr方法返回发出请求的客户机的IP地址
getRemoteHost方法返回发出请求的客户机的完整主机名
getRemotePort方法返回客户机所使用的网络端口号
getLocalAddr方法返回WEB服务器的IP地址。
getLocalName方法返回WEB服务器的主机名

获得客户机请求头
getHeader方法
getHeaders方法
getHeaderNames方法
获得客户机请求参数(客户端提交的数据)
getParameter方法
getParameterValues（String name）方法
getParameterNames方法
getParameterMap方法
```
三.request常见应用
```
获取浏览器类型
防盗链
各种表单输入项数据的获取
text、password、radio、checkbox、
file、select、textarea、 hidden、
image、button给js编程用
请求参数的中文乱码问题
```
四.HTTP响应
```
一个HTTP响应代表服务器向客户端回送的数据，它包括：
一个状态行、若干响应头、以及实体内容 ，其中的一些消息头和实体内容都是可选的，消息头和实体内容之间要用空行隔开。
  HTTP/1.1 200 OK--------------------------->状态行（状态行用于描述服务器对请求的处理结果。）

Server: Microsoft-IIS/5.0-------------------|
Date: Thu, 13 Jul 2000 05:46:53 GMT         |
Content-Length: 2291                        |----->多个消息头（消息头用于描述服务器的基本信息，以及数据的描述，服务器通过这些数据的描述信息，可以通知客户端如何处理等一会儿它回送的数据）
Content-Type: text/html                     |
Cache-control: private----------------------|
------------------------------------------------>一个空行
-------------------------------------------|
<HTML>                                     |---->实体内容(代表服务器向客户端回送的数据)
<BODY>-------------------------------------|
……
```
五.HTTP响应细节——常用响应头
```
HTTP请求中的常用响应头
Location: http://www.it315.org/index.jsp
Server:apache tomcat
Content-Encoding: gzip  
Content-Length: 80
Content-Language: zh-cn
Content-Type: text/html; charset=GB2312
Last-Modified: Tue, 11 Jul 2000 18:23:51 GMT
Refresh: 1;url=http://www.it315.org
Content-Disposition: attachment; filename=aaa.zip
Transfer-Encoding: chunked
Set-Cookie:SS=Q0=5Lb_nQ; path=/search
Expires: -1
Cache-Control: no-cache
Pragma: no-cache
Connection: close/Keep-Alive
Date: Tue, 11 Jul 2000 18:23:51 GMT
```
六.HTTP请求的细节—通用信息头
```
通用信息头指既能用于请求，又能用于响应的一些消息头。
Cache-Control: no-cache  
Pragma: no-cache   
Connection: close/Keep-Alive   
Date: Tue, 11 Jul 2000 18:23:51 GMT

```
