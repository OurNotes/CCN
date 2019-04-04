总操作流程：
- 1、下载安装
- 2、写代码
- 3、看效果

***

# 下载安装

```js
cnpm install vue-particles --save-dev
```

# 写代码

> 1、main.js添加
```js
import VueParticles from 'vue-particles'
Vue.use(VueParticles)
```

>2、要添加背景的组件添加代码

```html
  <div class="hello">
    <div class="msg">
      <h1>{{msg}}</h1>
    </div>
    <vue-particles color="#dedede" :particleOpacity="0.7" :particlesNumber="80" shapeType="circle" :particleSize="4"
      linesColor="#dedede" :linesWidth="1" :lineLinked="true" :lineOpacity="0.4" :linesDistance="150" :moveSpeed="3"
      :hoverEffect="true" hoverMode="grab" :clickEffect="true" clickMode="push">
    </vue-particles>
  </div>
```

```css
  .hello {
    position: relative;
  }
  .msg {
    position: absolute;
  }
```

# 看效果

运行看效果