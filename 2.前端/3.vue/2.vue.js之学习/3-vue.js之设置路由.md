总操作流程：
- 1、[删除初始化的一些文件](#vue.js-01)
- 2、[创建两个vue文件](#vue.js-02)
- 3、[修改router.vue文](#vue.js-03)


-------

# <a name="vue.js-01" href="#" >删除初始化的一些文件</a>
![](image/3-1.png)

- 项目结构：

![](image/3-2.png)

- 代码结构：

![](image/3-3.png)

# <a name="vue.js-02" href="#" >创建两个vue文件</a>

- index.vue

```vue
<template>
  <div>index page</div>
</template>
```
- content.vue

```vue
<template>
  <div>content page</div>
</template>
```
# <a name="vue.js-03" href="#" >修改router.vue文件</a>
```vue
import Vue from 'vue'
import Router from 'vue-router'
import Index from '@/components/page/index'
import Content from '@/components/page/content'

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      component: Index
    }, {
      path: '/content/:id',
      component: Content
    }
  ]
})
```
