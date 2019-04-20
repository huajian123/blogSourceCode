---
title: springbootHttp
date: 2019-04-18 22:36:39
categories: 
- Java
- SpringBoot
tags:
- Java
- SpringBoot
---
### 简单的Get请求
```
@RestController
public class GetController {
    private Map<String, Object> params = new HashMap<>();
    
    @RequestMapping(path = "/{city_id}/{user_id}",method = RequestMethod.GET)
    public Object findUser(@PathVariable("city_id") String cityId, @PathVariable("user_id") String userId) {
        params.clear();
        params.put("cityId", cityId);
        params.put("userId", userId);
        return params;
    }
}
```
### 省略方法的Get请求
```
  @GetMapping(value = "/v1/page_user1")
    public Object pageUser(int from, int size) {
        params.clear();
        params.put("from", from);
        params.put("size", size);
        return params;
    }
```
