---
title: 浅谈 Web Components
date: 2022-09-02 14:57:01
categories: Front
tags:
---

# Web Components
## 是什么
随着前端框架的流行，组件化开发已经趋于常态，我们通常会把功能通用的模块抽取然后封装成单个组件，这样使用和维护起来都会变得更加简单。但组件也受限于框架，例如一旦离开框架本身，组件就无法使用了，那有没有跨越框架范围的技术构建通用的组件呢？有的，就是今天要介绍的 Web Components。
> Web components are a set of web platform APIs that allow you to create new custom, reusable, encapsulated HTML tags to use in web pages and web apps.

Web Components 是一套 Web API，允许你创建能在 Web 页面和应用中使用的自定义、可重用、封装的 HTML 标签。总体上来说 Web Components 是 “通过一种标准化的非侵入的方式封装一个组件”。Web Components 的概念最早由 Alex Russell 在2011年的 Fronteers大会上首次提出，2013年 Google 发布了 Polymer 框架，是基于 Web Components API 的实现，来推动 Web Components 的标准化。 2014 年的时候 Chrome 发布了早期的 v0 级别的组件规范，目前已更新到 v1 版本，被各大浏览器接受并支持。

## 有什么
- HTML templates
HTML 内的 DOM 模板，在 template 元素内声明，内联样式 style 需要放置在它的内部，模板技术引入了两个重要的元素 template 和 slot ，template 提供模板的功能，slot 则被用来提供一个占位符号，使 template 更灵活。
template 标签本质上合 HTML 内置标签是一样的，但在 template 标签被激活前：
  - 标签不会被渲染，标签的内容也是会被隐藏 ，页面上看不到标签展示效果
  - 模板里的内容不会有副作用，例如 script 标签里不的脚本不会执行，图片不会加载，视频不会播放
  - 基本上可以放置于任何节点上，例如 header、body 等；激活一个 template 最简单的方式是对它的内容做个深拷贝，然后再插入节点中，举个🌰：

## 技术优点
### 原生支持
原生支持意味着可以不需要任何框架即可完成开发，同时也意味着这将有更好的用户体验，更低的网络请求，以及更稳定的迭代前景。并且我们一直都有在使用这项技术，比如 input， video，select 等等，其实他们都是标准的原生组件，只是如今我们自己也可以使用这项技术去创造这些组件。

### 无排他性
这是原生支持的一个延伸表现，作为浏览器原生支持也就意味着它可以在任何环境中使用，例如在 React，Angular，Vue 中使用他们。同时也意味着对 Web Components 的支持无需大刀阔斧的颠覆现有逻辑体系，你可以从局部开始进行改造。

### 无依赖性
这一点同样是原生支持的一个延伸表现，通过提供连接特定 Web 组件的选项，而无需将框架的依赖项导入到项目中，您就可以拥有优于流行框架的优势。
想象一下：如果您喜欢用 React 创建的小部件，并且想将其包含在您的项目中，则必须首先包含整个 React 库，然后才能导入您喜欢的小部件。相反，如果您选择使用 Web 组件创建的小部件，您可以立即将其插入到项目中——这一切都归功于这项技术的原生特性。