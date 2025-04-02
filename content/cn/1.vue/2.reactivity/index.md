---
ogImage: true
---

# 响应式 第1部分

Vue 提供了[优秀的响应式系统](https://vuejs.org/guide/essentials/reactivity-fundamentals.html)，它能跟踪数据的变化并自动触发更新，使你的 UI 始终与数据保持同步。Vue 的响应式系统提供了几个基本原语：`ref`、`reactive`、`computed` 和 `watch`。

- [`ref()`](https://vuejs.org/api/reactivity-core.html#ref) 创建一个容器来保存单个值，当值变化时会自动被跟踪。可以通过 `.value` 属性访问或更新该值。

- [`computed()`](https://vuejs.org/api/reactivity-core.html#computed) 接收一个 getter 函数并返回一个 `ref` 对象，该对象反映了 getter 函数的返回值。

在这个操作环境中，我们创建了一个名为 `count` 的 ref 对象来保存一个数字，以及一个名为 `double` 的计算属性，用于计算 `count` 的两倍。Vue 会智能地识别出 `double` 依赖于 `count`，因此每当 `count` 发生变化时，`double` 会自动重新计算。

尝试点击按钮增加 `count` 的值 - 你会看到 `double` 的值也相应地改变了。

::note
**注意**：在 `<template>` 中引用时，Refs 会被 Vue [自动解包](https://vuejs.org/guide/essentials/reactivity-fundamentals.html#declaring-reactive-state-1)。只有在 `<script>` 或 Vue 组件外的 JavaScript 中访问 ref 时才需要使用 `.value`。
::

## 挑战

现在让我们亲自动手！尝试修改代码，使乘数也能响应式地更新（当前硬编码为 `2`）。

你可以这样做：

1. 使用 `ref()` 创建一个名为 `multiplier` 的变量并设置为 `2`
2. 在 `<script>` 和 `<template>` 中将 `double` 重命名为 `result`
3. 更新 `result` 的实现，返回 `count.value * multiplier.value`{lang=js}
4. 添加另一个按钮来增加 `multiplier` 的值

就是这样！现在当你点击乘数按钮时，你将看到结果随着新的乘数而变化。

如果你遇到困难，可以点击下面的按钮或编辑器右上角查看解决方案。

:ButtonShowSolution{.bg-faded.px4.py2.rounded.border.border-base.hover:bg-active.hover:text-primary.hover:border-primary:50}

随意尝试更多想法！完成后，让我们继续下一部分，了解更多关于响应式系统的内容。
