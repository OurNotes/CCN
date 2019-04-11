总操作流程：
- 1、写代码
- 2、测试

***

# 写代码

>路由设置
```js
import Vue from 'vue'
import Router from 'vue-router'

import Login from '@/components/login/Login'
import MenuContainers from '@/components/home/MenuContainers'

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/home',
      name: 'menuContainers',
      component: MenuContainers,
      meta: { 
        requireAuth: true,
        title: "首頁",
        keepAlive: false
      }
    },
    {
      path: '/',
      name: 'login',
      component: Login,
      meta: { 
        title: "登录",
        keepAlive: true 
      }
    }
  ]
})
```

>在main.js最后添加(要在vue实列前设置)
```
router.beforeEach((to, from, next) => {
  if (to.matched.some(record => record.meta.requireAuth)) {
    if (sessionStorage.getItem('user') != null) {
      next();
    } else {
      next({
        path: '/',
        redirect: to.fullPath
      });
    }
  } else {
    next();
  }
});

new Vue({
  el: '#app',
  router,
  i18n,
  components: {
    App
  },
  template: '<App/>'
})
```

>在主组中的方法引用
```js

if (this.login) {
            let userObj = {
                name: this.form.userid,
                pwd: this.form.userpassword,
            }
              sessionStorage.setItem("user",JSON.stringify(userObj))
              this.$router.push('/home');
```


# 测试

运行测试