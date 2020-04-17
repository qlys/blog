---
title: markdown语法
date: 2020-04-17 15:30:54
tags:
categories: 
  - mardown
---

Markdown标签必须是在英文状态下才会生效,而且标签后需要跟一个空格
 <!-- more -->


## 基础
### 标题
```markdown
  # 标题一
  ## 标题二
  ### 标题三
  #### 标题四
  ##### 标题五
  ###### 标题六
```
### 段落
  段落的前后要有空行，所谓的空行是指没有文字内容。若想在段内强制换行的方式是使用两个以上空格加上回车（引用中换行省略回车）。
### 链接
  链接可以由两种形式生成：行内式、参考式、自定义链接、锚点
  ```markdown
  格式:[alt](URL title)
  行内式：
    [GitHub](https://github.com "GitHub")。

  参考式：
    [GitHub][1]
    [1]:https://https://github.com "GitHub"

  自定链接:
    baidu.com或者<baidu.com>

  锚点:
  [alt](#readme)
  ```
### 图片
```markdown
格式:![alt](URL title)
  ![图片](https://avatars0.githubusercontent.com/u/23652432?s=60&v=4 '自定义图片')
```


## 格式化
### 文本格式化
```markdown
  *斜体*,_斜体_
  **粗体**,__粗体__
  ~斜体~,~~斜体~~
```
### 区块引用
```markdown
在段落的每行或者只在第一行使用符号>,还可使用多个嵌套引用，如：
  > 引用一
  >> 引用二
  >>> 引用三
```
### 代码区块
```
  &#96;&#96;&#96;css
    .style{
      padding:1px;
    }
  &#96;&#96;&#96;

  快捷键效果`ctrl+c`
```


## 列表
```markdown
  无序列表*,+,_
  * 列表1
  * 列表2

  有序列表1.
  1. 列表1
  2. 列表2
```


## 表格
```markdown
标题1|标题2|标题3
-|-|-
表格1|表格2|表格3
表格4|表格5|表格6
表格7|表格8|表格9
```


## 水平线
```markdown
  *******
  -------
```

## 转义
```markdown
  \ 添加反斜杠转义
```