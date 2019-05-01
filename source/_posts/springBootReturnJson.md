---
title: 【SpringBoot】jackson处理方法
date: 2019-05-01 15:42:16
categories: 
- Java
- SpringBoot
tags:
- Java
- SpringBoot
---
```
1）age字段如果为空的时候就不返回给前端
2）pwd 不返回给前端
3）phone 用account别名来返回给前端
4）日期格式化
public class User {
    @JsonInclude(JsonInclude.Include.NON_NULL)
    private int age;
    
    @JsonIgnore
    private String pwd;
    
    @JsonProperty("account")
    private String phone;
    
    @JsonFormat(pattern = "yyyy-MM-dd hh:mm:ss",locale = "zh",timezone = "GMT+8")
    private Date createTime;
    
    public User(int age, String pwd, String phone, Date createTime) {
        this.pwd = pwd;
        this.phone = phone;
        this.createTime = createTime;
    }
    .....
 }
 
 
```
