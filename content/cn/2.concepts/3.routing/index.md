---
ogImage: true
---

# 路由

## 基于文件的路由

基于文件的路由是 Nuxt 的核心功能之一。\
`pages/` 目录中的每个 Vue 文件对应一个 URL（路由）并渲染其内容。\
例如，`pages/index.vue` 对应 `/`，而 `pages/foo.vue` 对应 `/foo`。\
这个路由系统基于 [vue-router](https://router.vuejs.org/)。

此外，Nuxt 通过代码分割和其他技术优化每个页面，确保只传送请求路由所需的最小 JavaScript 代码。

## 导航

一旦你在 `pages/` 目录中创建了路由，你可以使用 `<NuxtLink>` 组件进行导航。

`<NuxtLink>` 组件允许你使用 `to` 属性指定路由来创建链接。\
与使用带有 `href` 属性的 `<a>` 标签相比，`<NuxtLink>` 自动优化导航，实现更快的页面过渡。

## 路由参数

在 `/pages` 目录中，你可以通过将文件名的一部分包装在 `[]` 中来定义动态路由。\
例如：`pages/posts/[id].vue`。

可以通过 `useRoute()` 访问 `[]` 中的路由参数。

```vue
<!-- pages/posts/[id].vue -->
<script setup lang="ts">
const route = useRoute()

// 当访问 /posts/1 时，route.params.id 的值将为 1
console.log(route.params.id)
</script>
```

## 挑战

尝试实现 `/posts/[id]` 路由，并启用从 `/` 和 `/foo` 到 `/posts/[id]` 的导航。\
此外，在 `/posts/[id]` 中，从路由参数读取 `id` 并在屏幕上显示它。

### 完成步骤：

1. 在 `pages/posts/[id].vue` 中，使用 `useRoute()` 从 `params` 获取 `id` 并在屏幕上显示它。
2. 在 `pages/index.vue` 和 `pages/foo.vue` 中，使用 `<NuxtLink>` 创建导航到 `/posts/[id]` 的链接。\
   例如，创建一个导航到 `/posts/1` 的链接（你可以使用任何值）。

如果你遇到困难，可以点击下面的按钮或编辑器右上角的按钮查看解决方案。

:ButtonShowSolution{.bg-faded.px4.py2.rounded.border.border-base.hover:bg-active.hover:text-primary.hover:border-primary:50}

---

本节介绍的 `useRoute` 函数和 `<NuxtLink>` 组件由 Nuxt 的自动导入功能自动导入，因此你不需要手动导入它们。\
在下一节中，我们将详细探讨[自动导入](/concepts/auto-imports)。
