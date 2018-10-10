总操作流程：
- 1、[下载安装](#vue.js-01)
- 2、[搭建大型单页应用](#vue.js-02)
- 3、[安装并运行](#vue.js-03)
- 4、[测试](#vue.js-04)

----------

# <a name="vue.js-01" href="#" >下载安装</a>
```shell
cnpm install vue -g
```
# <a name="vue.js-02" href="#" >搭建大型单页应用</a>
```shell
cnpm install --global vue-cli -g # 全局安装 vue-cli

vue init webpack my-project # 创建一个基于 webpack 模板的新项目

剩下的默认就行
```
# <a name="vue.js-03" href="#" >安装并运行</a>
```shell
cd my-project
cnpm install
cnpm run dev
```
# <a name="vue.js-04" href="#" >测试</a>
访问 http://localhost:8080/

**ctrl+c ：退出**