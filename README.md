# spring cloud 学习

## 提示

spring-cloud-eureka-server : 服务注册服务器，主要用于服务注册与发现
	一般一个项目甚至一个公司一个，基本不需要修改
spring-cloud-eureka-client : 基本业务服务包装，大多数业务逻辑都在此实现

spring-cloud-zuul:相当于Nginx，用于对服务的代理，一般将授权检查、日志记录之类的代码放在这里

	

- pom使用模块开发，在该目录的pom里配置了项目的顶级parent。
- 运行请先运行server再运行其他
- 所有的模块基本上都加了eureka-client
- 运行eureka的高可用形式，要以不同的profile来运行。

peer1,peer2是指定的域名配置。本地需要增加localhost

    ```
    java -jar spring-cloud-eureka-server-0.0.1-SNAPSHOT.jar --spring.profiles.active=peer1  
    java -jar spring-cloud-eureka-server-0.0.1-SNAPSHOT.jar --spring.profiles.active=peer2
    ```

## 端口

- config-server : 8888,8887,8886
- config-client : 8082,8087
- eureka-server : 8761，8762
- eureka-client : 8083,8084,8085 （构建负载均衡集群）内容提供者
- eureka-consumer : 8086 （用来消费 eureka-client 提供的服务）
- eureka-consumer-hystrix : 8086 
- zuul - 8088