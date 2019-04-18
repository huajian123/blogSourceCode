---
title: 【Angular】Http
date: 2019-04-18 11:17:26
tags: 
- Angular 
- Angular小知识
categories: 
- Angular
- Angular小知识
---
### 跳过拦截器
方法一
```
import { Injectable } from '@angular/core';
import { HttpClient, HttpBackend } from '@angular/common/http';

@Injectable()
export class AnonymousRequestService {
  // 注入 HttpBackend 
  constructor(private httpBackend: HttpBackend) { }

  requestByNewHttpClient() {
    // 建立新的 HttpClient 
    const newHttpClient = new HttpClient(this.httpBackend);
    return this.httpClient.get('https://jsonplaceholder.typicode.com/todos/3');
  }
}
```
方法二
```
请求时
this.httpClient.get(
  'https://jsonplaceholder.typicode.com/todos/2', 
  // 添加 Anonymous 的 header
  { headers: { 'Anonymous': '' } }
);
在拦截器中
public intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
  // 如果 header 被加料過，把它移除，並不進行原本要處理的行為
  if (req.headers.get('Anonymous') !== undefined) {
    const newHeaders = req.headers.delete('Anonymous')
    const newRequest = req.clone({ headers: newHeaders });
    return next.handle(newRequest);
  } else {
    const newRequest = req.clone({ setHeaders: { 'Authorization': 'Bearer fakeToken' } });
    return next.handle(newRequest);
  }
}
```
