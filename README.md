# kaka
一个简易的mvc框架，包含IOC和AOP功能

# kaka使用手册
kaka是我写的一个小型mvc框架。

麻雀虽小, 五脏俱全！

kaka不仅是一个mvc框架，其中还包括了IOC和AOP等功能。

## DEMO
### web.xml中配置
首先配置一个Filter，用来拦截所有请求。
Filter类为：com.kaka.core.KakaGo
 
```
<filter>
	<filter-name>go</filter-name>
	<filter-class>com.kaka.core.KakaGo</filter-class>
</filter>
<filter-mapping>
	<filter-name>go</filter-name>
	<url-pattern>/*</url-pattern>
</filter-mapping>
```

然后，配置几个初始化参数

- 首页（indexPage）
```
<!-- 首页不拦截 -->
<context-param>
	<param-name>indexPage</param-name>
	<param-value>index.jsp</param-value>
</context-param>
```
- 静态资源（staticResource）
```
<!-- 静态资源不拦截 -->
<context-param>
	<param-name>staticResource</param-name>
	<param-value>lib</param-value>
</context-param>
```

- 配置要扫描的包（scanPackage）（其中包括使用注解的类）
```
<!-- 配置要扫描的包 -->
<context-param>
	<param-name>scanPackage</param-name>
	<param-value>com.gcl.kaka</param-value>
</context-param>
```
- 最后，添加所需jar包
    - kaka.jar
    - log4j.jar

OK，配置完成

注解：
- Action
Action用来配置请求方法
    - 1，方法必须为public
    - 2，参数必须是：HttpServletRequest req, HttpServletResponse resp
    - 3，必须返回一个字符串，为页面名称，如果返回json数据，请返回“ajax”
 

- Controller
    - Controller类必须有一个午餐构造函数
 

- Service
    - Service 标注的类必须有一个无参构造函数

- Inject
    - 标注属性的类型必须用Service注解，否则报错
        - Aop相关注解
            - Before（“xxx”）
            - After（“xxx”）
            - Around（“xxx”）

## 好了，没啦！

