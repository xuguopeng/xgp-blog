---
id: event-loop
title: JavaScript event loop 事件循环
slug: /
---

## 一. JavaScript 单线程

JavaScript 最大的特点就是单线程，同一时间只能做同一件事，JavaScript 作为浏览器脚本语言，主要用途是和用户互动和操作dom， 这就决定了它只能是单线程。例: 假如JavaScript是多线程，一个线程在dom上添加内容，一个线程在删除dom节点，浏览器就不知道以哪个线程为准了。

为了利用多核CPU的计算能力，HTML5 提出了 Web Worker标准，允许JavaScript脚本创建多线程，但是子线程受主线程控制，且不可操作dom。所以，这个新标准并没有影响JavaScript的单线程。

## 二. 任务队列

单线程就意味着任务是需要排队进行的，前一个任务结束，才执行下一个任务。如果一个任务耗时过长，后一个任务不得不等着上一个任务完成。