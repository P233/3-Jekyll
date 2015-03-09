# 3-Jekyll Theme

新版 3-Jekyll，当前完成度 80%，预览请访问 [http://peiwen.lu](http://peiwen.lu)，[Github repo](https://github.com/P233/P233.github.io)。

旧版请在 [https://github.com/P233/3-Jekyll/releases](https://github.com/P233/3-Jekyll/releases) 下载。


## 针对旧版的改进

* 侧边栏使用 Tag 做为文章分类，因为 Category 会转换为小写，而 Tag 大小写敏感。
* 自动生成侧边栏 Tag 分类，基本不需要修改模板文件。但 Tag 顺序由 Jekyll 根据时间顺序生成，需要手动调整 Tag 顺序只能修改 `_includes/sidebar.html`，格式是 `<li class="sidebar-tag" data-filter="TAG">TAG</li>`，替换 `TAG`，大小写敏感。
* 更加全面的 Sass 变量，方便个性化主题样式。
* 暂定取消文章的标题目录。
* 取消了嵌入 Codepen。


## TODO

* 搜索功能
* Webkit 换页动画
* 改进 Tag 筛选功能
* 集成 Google Analytics
* 博客文章时间归档
* Favicon

其他建议欢迎[提交 issue](https://github.com/P233/3-Jekyll/issues/new)


## 使用

### 设置 `_config.yml`

`_config.yml` 除基本的站点设置外，新加入了社交链接与评论设置。将需要添加的社交帐号填入对应设置，并取消注释，会在头像下方增加一条社交帐号的链接。支持 Twitter, Weibo, Github, Codepen 以及 Dribbble。此外，填入 Disqus 的 shortname 也会启用 Disqus 评论。

### 修改样式

样式相关的 Sass 变量都存储在 `/css/main.sass` 文件中，修改这个文件可以满足大部分样式定制的需求。建议首先修改 `$gradient-start` 与 `$gradient-end` 两个变量，给自己的博客使用独一无二的侧边栏背景。

### 替换图片

请不要忘记替换 `/assets/img/` 内的图片。`avatar.jpg` 是侧边栏头像的图片，`qrcode.jpg` 会在提示浏览器不兼容时使用。[QR Code 生成器](https://www.unitag.io/qrcode)
