总操作流程：
- 1、[写程序](#vue.js-01)
- 2、[测试](#vue.js-02)

***

# <a name="vue.js-01" href="#" >写程序</a>

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
import first from '@/components/first';
import second from '@/components/second';
import third from '@/components/third';
export default {
        data () {
             return {
              first: "first", 
              second: "second",
              third: "third",
              currentView: 'first',
             };
         },
         components: { 
             first,
             second,
             third
         },
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

# <a name="vue.js-02" href="#" >测试</a>

![](image/14-1.gif)