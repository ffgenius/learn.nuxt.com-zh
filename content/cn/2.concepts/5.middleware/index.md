---
ogImage: true
---

# 中间件

Nuxt 提供的中间件功能允许你在页面导航前执行自定义代码。
这个功能在需要根据用户登录状态限制页面访问等场景中特别有用。

中间件分为两种类型：全局中间件和命名路由中间件。
这两种类型都在项目的 `middleware` 目录中定义。

## 全局中间件

全局中间件会在每次路由导航时自动执行，定义方式如下：

```
├── middleware/
│   └── hello.global.ts
```

```ts
// middleware/hello.global.ts
export default defineNuxtRouteMiddleware(() => {
  console.log('hello')
})
```

## 命名路由中间件

命名路由中间件可以按如下方式定义：

```
├── middleware/
│   └── helloA.ts
```

```ts
// middleware/hello.ts
export default defineNuxtRouteMiddleware(() => {
  console.log('helloA')
})
```

```vue
<!-- pages/a.vue -->
<script setup lang="ts">
definePageMeta({
  middleware: ['hello'],
})
</script>

<template>
  <h1>Hello A</h1>
</template>
```

## 中间件执行时机

这些中间件函数不仅在客户端导航期间执行，而且在使用 SSR 或 SSG 渲染页面时也在服务器端执行。\
如果你在中间件内使用本地存储等客户端 API，你需要确保中间件仅在客户端运行。\
你可以使用 `import.meta` 确定执行环境。\
要跳过服务器端执行，可以使用 `import.meta.server`。

```ts
export default defineNuxtRouteMiddleware((to) => {
  // 在服务器端跳过中间件执行（等同于 if (import.meta.client) { ... }）
  if (import.meta.server)
    return

  // 一些处理
  window.localStorage.setItem('key', 'value')
})
```

## 挑战

创建一个从 `localStorage` 读取信息的中间件，并仅在存在特定值时允许访问 `/foo`。\
在这个例子中，我们将创建一个中间件，只有当键 `isSignedIn` 设置为 `true` 时才允许访问 `/foo`。\
此外，在 `index.vue` 中添加一个按钮，允许用户设置这个值。

:ButtonShowSolution{.bg-faded.px4.py2.rounded.border.border-base.hover:bg-active.hover:text-primary.hover:border-primary:50}
