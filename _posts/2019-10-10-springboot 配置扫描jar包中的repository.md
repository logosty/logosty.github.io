---
tags: [springboot,config]
title: springboot 配置扫描 jar 包中的 repository
key: blog_springboot_repository
pageview: true
comment: true
---

# 场景
a 模块中有使用自动导入
```java
@Autowired
private SageConfigRepository sageConfigRepository;
```
但是 SageConfigRepository 这个接口是在一个 jar 包中，由 maven 依赖引入的。直接启动项目会报错。

# 解决方法
在启动类加入注解
```java
@EnableJpaRepositories(basePackages = { "com.XXX" })
@EntityScan(basePackages = { "com.XXX" })
```



