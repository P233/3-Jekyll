---
layout: post
title: Css实现固定列表格
tags: Css
---

# 固定表格

index.html
```html
<!DOCTYPE html>
<html class="hb-loaded">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=Edge,chrome=1">
    <title id="page-title">
    </title>
    <meta name="viewport" content="width=device-width,height=device-height,inital-scale=1.0,maximum-scale=1.0,user-scalable=no;">
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <table class="manipulate" cellspacing="0">
      <tbody>
        <tr>
          <th class="roleInfotd">
            排序
          </th>
        </tr>
        <tr>
          <td colspan="1" align="center">
          </td>
        </tr>
        <tr>
          <td colspan="1" align="center">
          </td>
        </tr>
      </tbody>
    </table>
    <div class="table-container">
      <table class="roleList" cellspacing="0">
        <tbody>
          <tr>
            <!-- <th data-sort="id">序号</th> -->
            <th data-sort="name">名称</th>
            <th data-sort="enname">英文名称</th>
            <th>下属国家</th>
            <th>排序</th>
            <th>状态</th>
            <th>创建人</th>
            <th>创建时间</th>
          </tr>
          <tr>
            <td>下属国家下属国家下属国家</td>
            <td>排序</td>
            <td>状态</td>
            <td>创建人</td>
            <td>创建时间</td>
            <td>&nbsp;</td>
            <td>&nbsp;</td>
          </tr>
          <tr>
            <td>下属国家下属国家下属国家</td>
            <td>排序</td>
            <td>状态</td>
            <td>创建人</td>
            <td>创建时间</td>
            <td>&nbsp;</td>
            <td>&nbsp;</td>
          </tr>
        </tbody>
      </table>
    </div>
    <table class="manipulate" cellspacing="0">
      <tbody>
        <tr>
          <th class="roleInfotd">
            操作
          </th>
        </tr>
        <tr>
          <td colspan="1" align="center">
          </td>
        </tr>
        <tr>
          <td colspan="1" align="center">
          </td>
        </tr>
      </tbody>
    </table>
  </body>
</html>
```

style.css

``` css
@charset "UTF-8";
    * {
    margin:0;
    padding:0;
    list-style:none;
    font-family:'Microsoft Yahei','WenQuanYi Micro Hei Mono','WenQuanYi Micro Hei','Microsoft Yahei Mono',sans-serif,Simsun;
    outline:none none none none;
    -moz-box-sizing:border-box;
    box-sizing:border-box;
}
::-webkit-scrollbar {
    width:5px
}
::-webkit-scrollbar-track-piece {
    background-color:transparent
}
::-webkit-scrollbar-thumb {
    background:#ddd;
    border-radius:3px
}
.table-container {
    overflow-x:auto;
    overflow-y:hidden;
    vertical-align:top;
    display:inline-block;
    width:-moz-calc(100% - 8em);
    width:-webkit-calc(100% - 8em);
    width:calc(100% - 8em);
    margin:0 -0.6em;
    border-left:1px solid #cfdbe2;
}
.manipulate{
    vertical-align:top;
    width:auto;
    display:inline-block;
}

table {
    width:100%;
    height:auto;
    border-collapse:collapse;
    text-align:center;
}
tr {
    height:3.5em;
    background-color:#fff;
}
tr:nth-child(odd) {/*even*/
    background-color:#d9edf7;
}
td,th {
    border:1px solid #cfdbe2;
    max-width:150px;
    box-sizing:border-box;
    text-align:center;
    white-space:nowrap;
    text-overflow:ellipsis;
    overflow:hidden;
    padding:0 1em;
}
```






