---
title: Spring MVC 注解总结
date: 2018-03-04
---

        借鉴前人，简单对Spring MVC中的注解进行总结。
@RequestMapping
@RequestMapping用于处理请求地址映射（将请求映射到对应的控制器方法中），可用于类或方法上。用于类上，表示类中的所有响应请求的方法都是以该地址作为父路径。
@RequestParam
@RequestParam用于将请求参数区数据映射到功能处理方法的参数上。
@PathVariable
@PathVariable用于将请求URL中的模板变量映射到功能处理方法的参数上。
@ModelAttribute
@ModelAttribute可以应用在方法参数上或方法上，它的作用主要是当注解在方法参数上时会将注解的参数对象添加到Model中；当注解在请求处理方法Action上时会将该方法变成一个非请求处理的方法，但其它Action被调用时会首先调用该方法。
@SessionAttributes
在默认情况下，ModelMap中的属性作用域是request级别，也就是说，当本次请求结束后，ModelMap中的属性将销毁。如果希望在多个请求中共享ModelMap中的属性，必须将其属性转存到session中，这样ModelMap的属性才可以被跨请求访问。    Spring 允许我们有选择地指定 ModelMap中的哪些属性需要转存到session 中，以便下一个请求属对应的 ModelMap 的属性列表中还能访问到这些属性。    注：该注解不能放在方法上，只是放在类上。 
@Responsebody
@Responsebody表示该方法的返回结果直接写入HTTP response body中。一般在异步获取数据时使用，在使用@RequestMapping后，返回值通常解析为跳转路径，加上@Responsebody后返回结果不会被解析为跳转路径，而是直接写入HTTP response body中。比如异步获取json数据，加上@Responsebody后，会直接返回json数据。
@RequestBody
@RequestBody将HTTP请求正文插入方法中,使用适合的HttpMessageConverter将请求体写入某个对象。
@CookieValue
将请求的Cookie数据，映射到功能处理方法的参数上。
@ResponseStatus
定义处理器功能处理方法/异常处理器返回的状态码和原因。
@ExceptionHandler
注解式声明异常处理器。
@RestController
相当于@ResponseBody ＋ @Controller合在一起的作用。
未完，待补充。。。
参考[讲得很详细]
springmvc 注解总结
注解式控制器运行流程及处理器定义 第六章 注解式控制器详解——跟着开涛学SpringMVC
