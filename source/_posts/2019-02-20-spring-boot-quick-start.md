---
title: Spring Boot 入门
date: 2019-02-20
---

        使用spring boot可以非常方便、快速搭建项目，使我们不用关心框架之间的兼容性，适用版本等各种问题，我们想使用任何东西，仅仅添加一个配置就可以，所以使用spring boot非常适合构建微服务。
Spring Boot — BUILD ANYTHING
Spring Boot is designed to get you up and running as quickly as possible, with minimal upfront configuration of Spring. Spring Boot takes an opinionated view of building production-ready applications.
Spring Boot旨在尽可能快地启动和运行，只需最少的Spring前端配置。 Spring Boot对构建面向生产的应用程序有独到的观点。
Spring Boot 的优势
良好的基因
SpringBoot是伴随着Spring 4.0而生的，boot是引导的意思，也就是它的作用其实就是在于帮助开发者快速的搭建Spring框架，因此SpringBoot继承了Spring优秀的基因，在Spring中开发更为方便快捷。
简化编码
配合各种starter使用，基本上可以做到自动化配置
简化配置
Spring Boot摈弃了繁琐的xml配置文件，大量的配置文件经常是导致生产事故的原因。Spring Boot大量采用yml形式的配置文件再加上相应的Annotation，从而大大减少了配置文件的个数，因为以前的Spring应用引入一个第三方框架说不定就要添加一个配置文件。
简化部署
Spring Boot天生就是为了简单、快捷部署而生。SpringBoot内嵌了Tomcat，不需要额外部署应用服务器Tomcat，只需简单一个Java运行环境即可，而且启动的命令也非常简单：java –jar xxx-release.jar。同时Spring Boot结合现在非常火的技术 Docker、Kubernetes可以快速实现集群部署。
简化监控
Spring Boot集成了非常高效的监控框架，只要简单引入对spring-boot-start-actuator的依赖，就可以实现对服务性能的监控。结合Spring Cloud就可以实现对整个微服务链路的全天候监控。
HelloWorld准备环境在开始Spring Boot开发之前，需要先确认您的电脑上已经有以下环境：
JDK 8
Maven 3.0+
Intellij IDEA
创建maven工程12345678spring-boot-01-helloworldcom  +- tyron      +- HelloWorldMainApplication.java      |      +- controller      |  +- HelloController.java      |
引入web模块pom.xml中添加支持web的模块：
1234<dependency>    <groupId>org.springframework.boot</groupId>    <artifactId>spring-boot-starter-web</artifactId> </dependency>
编写一个主程序12345678910/** *  @SpringBootApplication 来标注一个主程序类，说明这是一个Spring Boot应用 */@SpringBootApplicationpublic class HelloWorldMainApplication &#123;    public static void main(String[] args) &#123;        // Spring应用启动起来        SpringApplication.run(HelloWorldMainApplication.class,args);    &#125;&#125;
编写相关的Controller12345678910@Controllerpublic class HelloController &#123;    @RequestMapping("/hello")    @ResponseBody    public String hello() &#123;        return "Hello World!";    &#125;&#125;
运行主程序启动主程序，打开浏览器访问http://localhost:8080/hello，就可以看到效果了！
总结使用spring boot可以非常方便、快速搭建项目，使我们不用关心框架之间的兼容性，适用版本等各种问题，我们想使用任何东西，仅仅添加一个配置就可以，所以使用spring boot非常适合构建微服务。
