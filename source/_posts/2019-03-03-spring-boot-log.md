---
title: Spring Boot与日志
date: 2019-03-03
---

        日志框架、日志配置示例代码
一、日志框架市场上存在非常多的日志框架。 JUL（java.util.logging），JCL（Apache Commons Logging），Log4j，Log4j2，Logback、 SLF4j、 jboss-logging等。Spring Boot在框架内容部使用JCL，spring-boot-starter-logging采用了 SLF4j 和 Logback 的形式，Spring Boot也能自动适配（jul、 log4j2、 logback） 并简化配置 。
二、SLF4j的使用2.1、如何在系统中使用SLF4j   https://www.slf4j.org开发过程中，日志记录方法的调用，不应该直接调用日志的实现类，而是调用日志抽象层里面的方法；
项目中导入 SLF4j 和 Logback 的jar包：
123456789import org.slf4j.Logger;import org.slf4j.LoggerFactory;public class HelloWorld &#123;  public static void main(String[] args) &#123;    Logger logger = LoggerFactory.getLogger(HelloWorld.class);    logger.info("Hello World");  &#125;&#125;
每一个日志的实现框架都有自己的配置文件。使用slf4j以后，配置文件还是使用日志实现框架自己本身的配置文件；
2.2、遗留问题a（slf4j+logback）: Spring（commons-logging）、Hibernate（jboss-logging）、MyBatis、xxxx
统一日志记录，即使是别的框架和我一起统一使用slf4j进行输出？
如何让系统中所有的日志都统一到slf4j；
1、将系统中其他日志框架先排除出去；
2、用中间包来替换原有的日志框架；
3、我们导入slf4j其他的实现
三、SpringBoot日志关系SpringBoot中的日志实现： spring-boot-starter  中的  spring-boot-starter-logging 实现
SpringBoot版本：2.1.3.RELEASE 结构图：
总结：
1）、SpringBoot底层也是使用slf4j+logback的方式进行日志记录
2）、SpringBoot也把其他的日志都替换成了slf4j；
3）、中间替换包？
​    举例：在jul-to-slf4j中均是使用 SLF4J 的实现类，log4j-to-slf4j也是如此
4）如果我们要引入其他框架？一定要把这个框架的默认日志依赖移除掉？
Spring框架用的是commons-logging；
12345678910<dependency>    <groupId>org.springframework</groupId>    <artifactId>spring-core</artifactId>    <exclusions>        <exclusion>            <groupId>commons-logging</groupId>            <artifactId>commons-logging</artifactId>        </exclusion>    </exclusions></dependency>
SpringBoot能自动适配所有的日志，而且底层使用slf4j+logback的方式记录日志，引入其他框架的时候，只需要把这个框架依赖的日志框架排除掉即可；
四、日志使用4.1、默认配置SpringBoot默认帮我们配置好了日志；
123456789101112131415161718192021//记录器Logger logger = LoggerFactory.getLogger(getClass());@Testpublic void contextLoads() &#123;    //System.out.println();    //日志的级别；    //由低到高   trace<debug<info<warn<error    //可以调整输出的日志级别；日志就只会在这个级别以以后的高级别生效    logger.trace("这是trace日志...");    logger.debug("这是debug日志...");    //SpringBoot默认给我们使用的是info级别的，没有指定级别的就用SpringBoot默认规定的级别；root级别    logger.info("这是info日志...");    logger.warn("这是warn日志...");    logger.error("这是error日志...");&#125;控制台输出INFO 7644 --- [  main] .t.s.SpringBoot03LoggingApplicationTests : 这是info日志...WARN 7644 --- [  main] .t.s.SpringBoot03LoggingApplicationTests : 这是warn日志...ERROR 7644 --- [  main] .t.s.SpringBoot03LoggingApplicationTests : 这是error日志...
修改SpringBoot的默认日志配置文件
12345678910111213logging.level.com.tyron = trace#logging.path=# 不指定路径在当前项目下生成springboot.log日志# 可以指定完整的路径；#logging.file=D:/springboot.log# 在当前磁盘的根路径下创建spring文件夹和里面的log文件夹；使用 spring.log 作为默认文件logging.path=/spring/log#  在控制台输出的日志的格式logging.pattern.console=%d&#123;yyyy-MM-dd&#125; [%thread] %-5level %logger&#123;50&#125; - %msg%n# 指定文件中日志输出的格式logging.pattern.file=%d&#123;yyyy-MM-dd&#125; === [%thread] === %-5level === %logger&#123;50&#125; ==== %msg%n
123456789日志输出格式：	%d表示日期时间，	%thread表示线程名，	%-5level：级别从左显示5个字符宽度	%logger&#123;50&#125; 表示logger名字最长50个字符，否则按照句点分割。 	%msg：日志消息，	%n是换行符   -->   %d&#123;yyyy-MM-dd HH:mm:ss.SSS&#125; [%thread] %-5level %logger&#123;50&#125; - %msg%n
logging.file
logging.path
Example
Description
(none)
(none)
只在控制台输出
指定文件名
(none)
my.log
输出日志到my.log文件
(none)
指定目录
/var/log
输出到指定目录的 spring.log 文件中
4.2、指定配置给类路径下放上每个日志框架自己的配置文件即可；SpringBoot就不使用他默认配置的了
Logging System
Customization
Logback
logback-spring.xml, logback-spring.groovy, logback.xml or logback.groovy
Log4j2
log4j2-spring.xml or log4j2.xml
JDK (Java Util Logging)
logging.properties
logback.xml：直接就被日志框架识别了；
logback-spring.xml：日志框架就不直接加载日志的配置项，由SpringBoot解析日志配置，可以使用SpringBoot的高级Profile功能
When possible, we recommend that you use the -spring variants for your logging configuration (for example, logback-spring.xml rather than logback.xml). If you use standard configuration locations, Spring cannot completely control log initialization.  —来自官方文档
1234<springProfile name="dev">    <!-- configuration to be enabled when the "staging" profile is active -->  	可以指定某段配置只在某个环境下生效</springProfile>
4.3、切换日志框架切换为 slf4j+log4j 的方式：
12345678910111213141516171819<dependency>  <groupId>org.springframework.boot</groupId>  <artifactId>spring-boot-starter-web</artifactId>  <exclusions>    <exclusion>      <artifactId>logback-classic</artifactId>      <groupId>ch.qos.logback</groupId>    </exclusion>    <exclusion>      <artifactId>log4j-over-slf4j</artifactId>      <groupId>org.slf4j</groupId>    </exclusion>  </exclusions></dependency><dependency>  <groupId>org.slf4j</groupId>  <artifactId>slf4j-log4j12</artifactId></dependency>
切换为 slf4j+log4j2的方式
123456789101112131415   <dependency>            <groupId>org.springframework.boot</groupId>            <artifactId>spring-boot-starter-web</artifactId>            <exclusions>                <exclusion>                    <artifactId>spring-boot-starter-logging</artifactId>                    <groupId>org.springframework.boot</groupId>                </exclusion>            </exclusions>        </dependency><dependency>  <groupId>org.springframework.boot</groupId>  <artifactId>spring-boot-starter-log4j2</artifactId></dependency>
