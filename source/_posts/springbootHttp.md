---
title: 【SpringBoot】请求
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
@PathVariable表示从路径中拿到参数并且一一对应

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
### 有默认值的Get请求
```
    在这里请求地址是localhost:8080/v2/page_user2?size=100&page=1000
    返回给前端的数据结构是
    {
        "size": 100,
        "from": 1000
    }
    1)在这里默认给page如果没有传值的时候给0
    2)page是对外需要传的参数，映射到from里面去

  @GetMapping(value="v2/page_user2")
    public Object pageUserV2(@RequestParam(defaultValue = "0", name = "page",required = true) int from, int size) {
        params.clear();
        params.put("from", from);
        params.put("size", size);
        return params;
    }
```

### 通过bean对象传参POST
```
postman中选择Post，body,JSON(application/json)
  /**
     * 使用bean对象传参
     * 需要指定http头为 content-type为application/json
     * @param user
     */
    @RequestMapping("/v3/save_user")
    public Object saveUser(@RequestBody User user) {
        params.clear();
        params.put("user", user);
        return params;
    }
```
### 获取Http头信息


```
// 在postman中提交时，参数headers里面给access_token的值
 @GetMapping("/v1/get_header")
    public Object getHeader(@RequestHeader("access_token") String accessToken, String id) {
        params.clear();
        params.put("access_token", accessToken);
        params.put("id", id);
        return params;
    }

```

### 使用HttpServletRequest来请求
```
  @GetMapping("v1/test_request")
    public Object testRequest(HttpServletRequest request) {
        params.clear();
        String id = request.getParameter("id");
        params.put("id", id);
        return params;
    }
```

### Post请求
```
@PostMapping("v1/test_post")
    public Object testPost(String id, String name) {
        params.clear();
        params.put("id", id);
        params.put("name", name);
        return params;
    }
```
