# Servlet开发 #

一：servletcontext详解

1.servlet的部署

```Java
      <web-app>
	<servlet>
		<servlet-name>AnyName</servlet-name>
		<servlet-class>HelloServlet</servlet-class>
	</servlet>
	<servlet-mapping>
		<servlet-name>AnyName</servlet-name>
		<url-pattern>/demo/hello.html</url-pattern>
	</servlet-mapping>
</web-app>
```

2.servlet接口实现类

    两个实现类：GenericServlet,HttpServlet

3.web服务器调用servlet的过程（重点）

```
web client              servlet container                      Httpservletreques       http servlet esponse          HttpServlet
|                               |                                       |                        |                        |
|                               |                                       |                        |                        |
|   1.http request(发送HTTP请求) |                                       |                        |                        |
------------------------------->|                                       |                        |                        |
|                               2.incept http request(接收请求)          |                        |                        |
|                               ----------------|                       |                        |                        |
|                               |               |                       |                        |                        |
|                               |《-------------|                       |                        |                        |
|                               |                                       |                        |                        |
|                               |3.newinstance(创建Httpservletreques对象)|                        |                        |
|                               |------------------------------------>  |                        |                        |
|                               |                                       |                        |                        |
|                               |            4.new instance             |                        |                        |
|                               |----------------------------------------------------------->   |                         |
|                               |                5.invoke service method(调用方法)                                         |
|                               |---------------------------------------------------------------------------------------> |
|                              |                                        |                                                 |
|                              |                                        |6.get request information(得到请求)               |  
|                             |                                         |<------------------------------------------------|
|                             |                                         |                          7.set response information(返回请求)
|                             |                                         |                       |<------------------------|
|8.http response              |
<------------------------------
```

4.Servlet其它细节

```Java
在Servlet的整个生命周期内，Servlet的init方法只被调用一次。
而对一个Servlet的每次访问请求都导致Servlet引擎调用一次servlet的service方法。
对于每次访问请求，Servlet引擎都会创建一个新的HttpServletRequest请求对象和一个新的HttpServletResponse响应对象，然后将这两个对象作为参数传递给它调用的Servlet的service()方法，service方法再根据请求方式分别调用doXXX方法。

<servlet>
		<servlet-name>invoker</servlet-name>
		<servlet-class>
			org.apache.catalina.servlets.InvokerServlet
		</servlet-class>
		<load-on-startup>2</load-on-startupa>
	</servlet>

```

5.Servlet的线程安全问题

```
当多个客户端并发访问同一个Servlet时，web服务器会为每一个客户端的访问请求创建一个线程，并在这个线程上调用Servlet的service方法，因此service方法内如果访问了同一个资源的话，就有可能引发线程安全问题。
如果某个Servlet实现了SingleThreadModel接口，那么Servlet引擎将以单线程模式来调用其service方法。
SingleThreadModel接口中没有定义任何方法，只要在Servlet类的定义中增加实现SingleThreadModel接口的声明即可。  
对于实现了SingleThreadModel接口的Servlet，Servlet引擎仍然支持对该Servlet的多线程并发访问，其采用的方式是产生多个Servlet实例对象，并发的每个线程分别调用一个独立的Servlet实例对象。
实现SingleThreadModel接口并不能真正解决Servlet的线程安全问题，因为Servlet引擎会创建多个Servlet实例对象，而真正意义上解决多线程安全问题是指一个Servlet实例对象被多个线程同时调用的问题。事实上，在Servlet API 2.4中，已经将SingleThreadModel标记为Deprecated（过时的）。
```

6.请求重定向和请求转发的区别

```
一个web资源收到客户端请求后，通知服务器去调用另外一个web资源进行处理，称之为请求转发。
一个web资源收到客户端请求后，通知浏览器去访问另外一个web资源，称之为请求重定向。
```
