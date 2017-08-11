---
layout: post
title: Vue2.0项目整合sentry
tags: 工具
---

### 一、Sentry是什么

Sentry 是一个开源的实时错误报告工具，支持 web 前后端、移动应用以及游戏，支持 Python、OC、Java 等等主流编程语言和框架 ，还提供了 GitHub、Slack、Trello 等常见开发工具的集成。Sentry 是个不错的日志监控工具。

### 二、Sentry可以做什么

可以实时监控网站错误报告并发送通知，Sentry中的通知有很多种默认情况是以邮件的形式发送通知。


### 三、Sentry怎么用

[Sentry Vue 文档][1] 此插件仅适用于Vue 2.0或更高版本。

Sentry官方集成了vue，但是官方文档在vue中的使用说明只有寥寥几行，仅仅说明了如何引入与集成简单的两步。
**如下：**

**1.安装**
```js
npm install raven-js --save
```
**2.导入并配置Raven.js和Raven.js Vue插件** 

```js
import Vue from 'vue';
import Raven from 'raven-js';
import RavenVue from 'raven-js/plugins/vue';

// Sentry 项目跟踪的key： 注册账号创建项目会得到一个key
Raven
    .config('https://1c20403dff0e42cd9d3b7b5fc2af851e@sentry.io/202597')
    .addPlugin(RavenVue, Vue)
    .install();
    
```

![此处输入图片的描述][2]

### 四、为什么要用Sentry
......



  [1]: https://docs.sentry.io/clients/javascript/integrations/vue/
  [2]: http://ouiqhbcw9.bkt.clouddn.com/_dji_screenshot_1502450515262.png
  
  
  
