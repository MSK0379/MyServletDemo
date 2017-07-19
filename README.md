# MyServletDemo
## Servlet简介
&emsp;&emsp;Servlet是运行在服务器的java应用程序，负责接受客户端的请求，和数据的处理，然后将结果发送给客户端的技术。  
&emsp;&emsp;sun公司jdk提供了一个servlet接口，然后提供了该接口的实现类HttpServlet，该Httpservlet类添加了能够解析   http协议的方法，并且重写了servlet接口的servlet方法，该方法中根据用户的http请求来判断是get提交或post提交，若get提交，调用doGet()方法，若post提交，调用doPost()方法
用户如果需要开发一个动态web资源，需要实现以下两个步骤：
- 编写应用程序（java类），然后继承Httpservlet重写其内部方法，
- 将应用程序部署到web服务器中，通过请求访问该应用程序，web服务器会调用该程序进行数	据处理。  
&emsp;&emsp;备注：上述应用程序即为一个servlet程序。
## servlet的生命周期（运行过程）
### 在下列时刻Servlet容器装载Servlet:

- 方式一：Servlet容器启动时自动装载Servlet。需要在web.xml文件中添加
```
<Servlet>
    <loadon-startup>1</loadon-startup>
      <!-- 数字越小优先级越高 -->
</Servlet
```
- 方式二：客户端请求某个servlet，web服务器会接受该请求，然后根据请求来实例化某个servlet。
- 方式三： Servlet类文件被更新后，重新装载Servlet
### 初始化
&emsp;&emsp;然后调用其内部的init()方法，进行初始化，并且只调用一次。  
&emsp;&emsp;再根据请求的数据提交方式，如果是get提交，调用doGet()方法，若post提交，调用doPost()方法。当web服务器关闭时，调用其destroy()方法来销毁该servlet。
