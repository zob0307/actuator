# actuator
spring boot actuator
https://www.jianshu.com/p/b0b40038bb93 


1.可以加入依赖

<dependency>    
  <groupId>org.springframework.boot</groupId>    
  <artifactId>spring-boot-starter-security</artifactId>
</dependency>

来保证actuator暴露接口的安全性，可以通过 -u 'user:password' 方式来访问basic auth

2.如果项目依赖的是springmvc框架，并且基础的配置文件是 application.yaml的话，可以增加 application.properties 文件来配置安全性的配置.

3.如果加入了security依赖，则所有的接口默认都需要被验证，如果只想 /admin路径下的请求进行验证，则需要加入配置

security.basic.enabled=true
security.basic.path=/admin
security.user.name=admin
security.user.password=password

4.如果项目依赖的是非springmvc框架的话， 需要在依赖中加入mvc的依赖

<dependency>    
  <groupId>org.springframework</groupId>    
  <artifactId>spring-webmvc</artifactId>
</dependency>

5.如果management.security.enabled的值是false的话，除开health接口还依赖endpoints.health.sensitive的配置外，其他接口都不需要输入用户名和密码了。

6.actuator暴露的health接口权限是由两个配置： management.security.enabled 和 endpoints.health.sensitive组合的结果进行返回的。

作者：LOC_Thomas
链接：https://www.jianshu.com/p/b0b40038bb93
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
