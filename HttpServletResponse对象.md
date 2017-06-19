# HttpServletResponse对象 #
一.response常见应用
```
案例1：302+location实现重定向
案例2：使用Refresh实现定时跳转
案例3：使用content-Type实现向浏览器输出图片
案例4：文件下载功能

通过response实现请求重定向。
请求重定向指：一个web资源收到客户端请求后，通知客户端去访问另外一个web资源，这称之为请求重定向。
应用场景：用户注册。
实现方式
response.sendRedirect()
实现原理：
302状态码和location头即可实现重定向
```
二.response细节
```
getOutputStream和getWriter方法分别用于得到输出二进制数据、输出文本数据的ServletOuputStream、Printwriter对象。
getOutputStream和getWriter这两个方法互相排斥，调用了其中的任何一个方法后，就不能再调用另一方法。  
Servlet程序向ServletOutputStream或PrintWriter对象中写入的数据将被Servlet引擎从response里面获取，Servlet引擎将这些数据当作响应消息的正文，然后再与响应状态行和各响应头组合后输出到客户端。
Serlvet的service方法结束后，Servlet引擎将检查getWriter或getOutputStream方法返回的输出流对象是否已经调用过close方法，如果没有，Servlet引擎将调用close方法关闭该输出流对象。
```
