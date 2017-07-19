# MyServletDemo
## Servlet简介
详情请查看个人博客[Servlet基础（一）](http://activeblog.xin/2017/07/19/Servlet%E5%9F%BA%E7%A1%80%EF%BC%88%E4%B8%80%EF%BC%89%EF%BC%9Aservlet%E7%9A%84%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F/)
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
- 方式三： Servlet类文件被更新后，重新装载Servlet。
运行提供的例程请注意web.xml文件
```
<!-- 测试方式一时不需要更改任何代码 -->
	<!-- 测试方式二时需要注释掉： -->
		<!--  <load-on-startup>2</load-on-startup> -->
		<!--  <servlet>
			    <description>Servlet生命周期测试二（优先级）</description>
			    <display-name>TestServlet2</display-name>
			    <servlet-name>TestServlet2</servlet-name>
			    <servlet-class>com.servlet.TestServlet2</servlet-class>
			    <load-on-startup>1</load-on-startup>
			      	 数字越小优先级越高
		 	 </servlet>
		 	 <servlet-mapping>
			    <servlet-name>TestServlet2</servlet-name>
			    <url-pattern>/TestServlet2</url-pattern>
			</servlet-mapping>-->
	<!-- 测试方式三：更改Servlet类的内容，在此不做过多解释，因为很少用到，当然你也可以在文件目录中更改类内容，但是要保证更改后不会编译、运行出错 。-->
```