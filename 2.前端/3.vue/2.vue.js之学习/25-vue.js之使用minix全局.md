总操作流程：
- 1、创建minix.js
- 2、创建测试代码
- 3、测试

***

# 创建minix.js

> 1、创建src\minix\minix.js
```js
import first from '@/components/first';
import second from '@/components/second';
import third from '@/components/third';
// src/mixins/index.js
let mixin = {

    data() {
        return {};
    },
    components: {
        first,
        second,
        third
    },
    methods: {

    }
};
export default mixin;
```
>2、配置main.js

```js
import GlobalImport from '../static/minix/GlobalImport.js'

Vue.mixin(GlobalImport)
```

# 创建测试代码

> 1、修改路由
```js
import Vue from 'vue'
import Router from 'vue-router'
import Test from '@/components/test'


Vue.use(Router)

export default new Router({
    routes: [{
        path: '/',
        name: 'Test',
        component: Test
    }]
})
```

> 2、test.vue

```html
<template>
  <div>
      <button @click="toggleTabs(first);">{{first}}</button>
      <button @click="toggleTabs(second);">{{second}}</button>
      <button @click="toggleTabs(third);">{{third}}</button>
      <component :is="currentView"></component>
  </div>

</template>

<script>

import GlobalImport from '../../../static/minix/GlobalImport';
export default {
        data () {
             return {
              first: "first", 
              second: "second",
              third: "third",
              currentView: 'first',
             };
         },
         mixins: [GlobalImport],
         methods: {
             toggleTabs (tabText) {
                 this.currentView = tabText;
             }
         }
    }
</script>


<style scoped>

</style>

```

> 3、first.vue

```html
<template>
    <div>我是第一个子组件</div>
</template>

<script >

</script>

<style scoped>

</style>
```

> 4、second.vue

```html
<template>
    <div>我是第二个子组件</div>
</template>

<script>

</script>

<style scoped>

</style>
```

> 5、third
```html
<template>
    <div>我是第三个子组件</div>
</template>

<script>

</script>

<style scoped>

</style>
```

# 测试

运行测试
