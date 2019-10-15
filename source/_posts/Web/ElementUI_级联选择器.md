---
title: elementUI 级联选择器
date: 2019-10-12 16:26:50
categories:
  - 前端
tags:
  - elementUI
---
### 使用elementUI 2.10.x ~ 2.12.x 版本的级联选择器会报 Level 错误

#### 解决方案

+ 将 `elementUI` 回退到 2.10.x 版本 <mark>或者</mark> 在清空级联选择器 `:options` 绑定数据前使用这句话

``` javascript
  this.$refs.cascader.panel.activePath = [];
```

#### 问题测试

+ 写一个最简单的的demo,注意加上 clearable 属性
+ 树结构数据直接使用官网提供的数据
+ 回到页面进行操作，先选中最后一级的某个数据，在点击清空按钮
+ 点开弹窗，会发现前几级仍然是高亮颜色，最后一级则是未选中时的颜色

#### 问题原因

+ 在这几个版本中，选中后数据后，以官网提供的方式清除 `v-model` 绑定变量值，会出现只清空当前选中数据的选中，而且关联父级的数据选中则没有处理，因此，此时如果清空 `:options` 绑定数据，也就导致了level的错误。
