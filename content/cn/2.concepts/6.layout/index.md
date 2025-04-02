---
ogImage: true
---

# 布局

Nuxt 提供了能够重用 UI 模式的功能。\
布局在 `~/layouts` 目录中实现，并使用 `app.vue` 中的 `NuxtLayout` 应用。\
每个页面可以通过使用 `definePageMeta` 指定布局。

```
├── layouts/
│   ├── default.ts
│   └── custom.ts
```

```vue
<!-- layouts/custom.vue -->
<template>
  <div>
    <p>Some default layout content shared across all pages</p>
    <slot />
  </div>
</template>
```

```vue
<!-- app.vue -->
<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>
```

```vue
<!-- pages/about.vue -->
<script setup lang="ts">
definePageMeta({
  layout: 'custom'
})
</script>
```
