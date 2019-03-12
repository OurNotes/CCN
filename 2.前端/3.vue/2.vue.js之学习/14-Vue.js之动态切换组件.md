总操作流程：
- 1、写程序
- 2、测试

***

# 写程序

> 1、test.vue

```html
<template>
  <div>
      <button @click="toggleTabs(first);">{{first}}</button>
      <button @click="toggleTabs(second);">{{second}}</button>
      <button @click="toggleTabs(third);">{{third}}</button>
      <component :is="currentView" keep-alive></component>
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

> 2、first.vue

```html
<template>
    <div>我是第一个子组件</div>
</template>

<script >

</script>

<style scoped>

</style>
```

> 3、second.vue

```html
<template>
    <div>我是第二个子组件</div>
</template>

<script>

</script>

<style scoped>

</style>
```

> 4、third
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

![](image/14-1.gif)