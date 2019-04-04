总操作流程：
- 1、[下载安装](#vue.js-01)
- 2、[写代码](#vue.js-02)
- 3、[看效果](#vue.js-03)

***

# <a name="vue.js-01" href="#" >下载安装</a>

```js
cnpm install vue-particles --save-dev
```

# <a name="vue.js-02" href="#" >写代码</a>

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

# <a name="vue.js-03" href="#" >看效果</a>

运行看效果