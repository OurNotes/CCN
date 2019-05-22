总操作流程：
方式一：
- 1、[下载js](#vue.js-01)
- 2、[配置](#vue.js-02)
- 3、[测试](#vue.js-03)
方式二：
- 1、下载js
- 2、配置
- 3、测试

***

# 方式一

### <a name="vue.js-01" href="#" >下载js</a>
[![](https://img.shields.io/badge/百度云-插件-green.svg "百度云 插件")](https://pan.baidu.com/s/1Mf0cO_2DgYPTqBPGEZBXIA)

提取码：a2a6

### <a name="vue.js-02" href="#" >配置</a>

> 1、将下载好的文件夹放到src文件夹下

> 2、写程序

- main.js写
```js
import Print from '@/plugs/print'
Vue.use(Print)
```

- html
```html
<template>
<section ref="print">
 打印内容
 <div class="no-print">不要打印我</div>
</section>
</template>
```

- 方法

```js
this.$print(this.$refs.print);
```

### <a name="vue.js-03" href="#" >测试</a>

运行测试