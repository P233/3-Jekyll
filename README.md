# 3-Jekyll Theme

欢迎任何改进建议，请直接[提交 issues](https://github.com/P233/3-Jekyll/issues/new)，感谢。

## 主要功能

* 不支持 IE9 及以下浏览器。
* 三列布局，最左侧是博客的 Tags 列表（需手动配置），点击后过滤相关文章，一篇文章可以给多个 tags 不会影响。
* 支持 pygments 代码高亮。
* 支持插入 Codepen。
* Lazy-load Disqus。
* 自动生成文章目录列表（h1-h3），鼠标移动到浏览器右侧边缘自动滑出（给每个标题重新生成一串随机字母做 ID，但这样可能会影响分享链接）。
* 支持移动设备，文章目录在移动设备上不显示。

同时制作了一份 Ghost 版本，请查看：[https://github.com/P233/3-Ghost](https://github.com/P233/3-Ghost)，你也可以移植给其他 Blog 平台，需遵守 MIT License。

**安装后需要做一些简单配置才可使用，请仔细阅读下面的说明：**

## 配置模板

### 模板文件

`/_layouts/index.html` 包含整个页面框架，以及左侧 sidebar 部分；`/index.html` 仅包含首页内容；`/_layouts/post.html` 包含文章内容布局，分享按钮，以及评论等等。

### 设置标签

这是修改模板最关键的一步。

1. 打开 `/_layouts/index.html` 文件找到 `<ul id="tags__ul"></ul>` 部分，将 `place_your_tag_display_name_here` 替换成 Tag 显示名称，别忘记修改 ID 顺序，完毕之后记录 tags 顺序以及总数。
2. 打开 `/assets/js/script.js` 找到 `// Variables` 部分，将 `place_your_tag_name_here` 替换成 tag 名称，这个名称需要与编辑文章时输入的 tag 一模一样，同时也需要满足 CSS 的 class 命名规则（不得已会影响命名 tag 的方式），顺序要与第一步匹配。
3. 在 js 文件中继续寻找 `// Tags switcher` 注释后面跟着的 `for`  循环，将 `i <= 6` 换成 tags 总数 + 1 (因为 No.1 是全部分类)。

### 搜索功能

搜索框目前只是摆设，请使用 [Google Custom Search Engine](https://www.google.com/cse/) 或 [jekyll-lunr-js-search](https://github.com/slashdotdash/jekyll-lunr-js-search) 插件。

### 修改头像

替换 `/assets/img/` 中的头像图片，`100px * 100px` 用于普通屏幕， `200px * 200px` 用于 Retina Display。

### 修改邮箱

通过 [Stop Link Spam Bots](http://www.safeemail.org/) 编辑了邮箱地址，希望能防 spam。

### Icon-font

使用了 [Fontello icon fonts generator](http://fontello.com)，并附上了 config 文件放置在 `/assets/font/` 中，方便替换图标。

### 代码高亮

支持 pygments 代码高亮，配色使用的是 [https://gist.github.com/edwardhotchkiss/2005058](https://gist.github.com/edwardhotchkiss/2005058) 并基于 [prism.js Coy theme](http://prismjs.com/download.html) 修改，文件位置在 `/assets/_sass/_pygments.scss` 中。

### Embedding Codepen

如果需要插入 Codepen，只需将 embed code 中的 `<p>` 部分粘贴在正文中，而不必粘贴 `<script>` 部分。更多关于插入 Codepen 的解释请查看 http://blog.codepen.io/documentation/features/how-do-i-embed-a-pen-on-another-site/ 。

如果完全不需要这个功能可以将 `/assets/js/script.js` 中的相关代码删除。

### 修改分享链接地址

打开 `/_layouts/post.html` 将分享链接中的 `place_your_url_here` 提换成博客地址。

### 修改许可协议

在 `/_layouts/post.html` 文件的分享链接部分声明博客内容所使用的许可协议，默认使用 [Attribution-NonCommercial-ShareAlike 3.0 Unported](http://creativecommons.org/licenses/by-nc-sa/3.0/)。

### Disqus 评论

Disqus 评论加载比较慢，所以使用了 lazy-load 的方式，在 `/assets/js/script.js` 的最下方找到 Disqus 相关代码，将 `window.disqus_shortname` 的值修改为自己的 shortname 。每篇文章的发表时间（`{{ page.date | date: "%Y%m%d" }}`）作为 identifier。

### 调整配色

个人非常不擅长配色，所以在 `/assets/_sass/style.scss` 文件中尽可能多地定义了颜色变量方便大家修改配色。关于默认的主题配色也请大家多提建议。

### 设置 RSS

请不要忘记编辑 `rss.xml` 文件，语言可填 `zh-cn` 或 `zh-tw`。

## 已知问题

1. 键盘 <kbd>Space</kbd> <kbd>PgUp</kbd> <kbd>PgDn</kbd> <kbd>↑</kbd> <kbd>↓</kbd> 等快捷键无效，这是由于当前的布局方式影响的。iOS7 Mobile Safari 自动隐藏地址栏也会无效。

## Credits

* [jquery-pjax](https://github.com/defunkt/jquery-pjax)
* [NProgress.js](http://ricostacruz.com/nprogress/)
* [Solarized Light Pygments CSS](https://gist.github.com/edwardhotchkiss/2005058)

## Copyright & License

Copyright (c) 2013 Peiwen Lu - Released under The MIT License.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.