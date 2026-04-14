# Spring Boot 配置

> **发表于**：2019-02-23　　**分类**：技术　　**标签**：springboot　　**原文**：[http://tyronblog.com/2019/02/23/spring-boot-config/](http://tyronblog.com/2019/02/23/spring-boot-config/)

---

讲解 Spring Boot 的配置文件

### 1、配置文件

Spring Boot使用一个全局的配置文件

- application.properties
- application.yml

配置文件放在`src/main/resources`目录或者类路径 /config 下

**yml**是 **YAML**（YAML Ain’t Markup Language）语言的文件，以数据为中心，比 json、xml 等更适合做配置文件

[http://www.yaml.org/](http://www.yaml.org/) 参考语法规范

全局配置文件的可以对一些默认配置值进行修改

YAML ： 配置例子

```yaml
server:
  port:
```

XML ：配置例子

```xml
<server
	<port
</server
```

### 2、YAML语法

#### 1、基本语法

- 使用缩进表示层级关系
- 缩进时不允许使用Tab键，只允许使用**空格**
- 缩进的空格数目不重要，只要相同层级的元素左侧对齐即可
- 大小写敏感

#### 2、YAML 支持的三种数据结构

- 字面量：单个的、不可再分的值
- 对象：键值对的集合
- 数组：一组按次序排列的值

##### 2.1、字面量

- 数字、字符串、布尔、日期
- 字符串
默认不使用引号
- 可以使用单引号或者双引号，单引号会转义特殊字符，双引号不会转义
- 字符串可以写成多行，从第二行开始，必须有一个单空格缩进，换行符会被转为空格。

name:   “zhangsan \n lisi”：输出；zhangsan 换行  lisi

name:   ‘zhangsan \n lisi’：输出；zhangsan \n  lisi

##### 2.2、对象（Map）

- 对象的一组键值对，使用冒号分隔。如：username: admin
- 冒号后面跟**空格**来分开键值
- {k: v}是行内写法

行内写法：

```yaml
friends:
```

##### 2.2、数组（List、Set）：

一组连词线（-）开头的行，构成一个数组，[]为行内写法

```yaml
pets:
```

#### 3、配置文件值注入

注入类：

```java
/** 
 * 将配置文件中配置的每一个属性的值，映射到这个组件中
 * @ConfigurationProperties
 *       prefix = "person"：配置文件中哪个下面的所有属性进行一一映射
 * 
 * 只有这个组件是容器中的组件，才能容器提供的@ConfigurationProperties
 */
@Component
@ConfigurationProperties
public

    private
    private
    private
    private

    private
    private
    private
    
    getter/setter
}
```

yaml配置文件：

```yaml
person:
  name:
  age:
  boss:
  birth:
  maps:
    hello:
    say:
  lists:
  animal:
    name:
    age:
```

打印：

```java
Person{name='xiaoming'
```

---

> **版权声明**：本文采用 [CC BY-NC-SA 3.0](https://creativecommons.org/licenses/by-nc-sa/3.0/) 许可协议，转载请注明出处。