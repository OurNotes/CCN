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

>在main.js最后添加
```
router.beforeEach((to, from, next) => {
  console.log("拦截");
  if (to.matched.some(res => res.meta.requireAuth)) { // 验证是否需要登陆
    if (sessionStorage.getItem('user')) { 
      next();
    } else {
      next({
        path: '/',
        query: {redirect: to.fullPath}
        });
    }
  } else {
    next();
  }
});
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