---
layout: post
title: Vue项目使用sentry
tags: 工具
---


文档地址: https://docs.sentry.io/clients/javascript/integrations/vue/

注意：此插件仅适用于Vue 2.0或更高版本。

**安装**
```js
npm install raven-js --save
```
**导入并配置Raven.js和Raven.js Vue插件**

```js
import Vue from 'vue';
import Raven from 'raven-js';
import RavenVue from 'raven-js/plugins/vue';

Raven
    .config('https://<key>@sentry.io/<project>')
    .addPlugin(RavenVue, Vue)
    .install();
    // <key>:Sentry 项目跟踪的key
```
