操作总流程：
- 1、[下载安装node.js](#node.js-01)
- 2、[配置node.js环境](#node.js-02)
- 3、[在doc下测试node.js是否成功](#node.js-03)
- 4、[安装淘宝 NPM 镜像](#node.js-04)
- 5、[使用 cnpm 安装 webpack](#node.js-05)


----------
# <a name="node.js-01" href="#" >下载安装node.js</a>
[![](https://img.shields.io/badge/官网-Node.js-red.svg "官网 Node.js")](https://nodejs.org/en/)

# <a name="node.js-02" href="#" >配置node.js环境</a>
在path添加node.js的路径：D:\nodejs
# <a name="node.js-03" href="#" >在doc下测试node.js是否成功</a>
```
node --version
```
# <a name="node.js-04" href="#" >安装淘宝 NPM 镜像</a>
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
`更新命令：npm install -g npm`

# <a name="node.js-05" href="#" >使用 cnpm 安装 webpack</a>
```
cnpm install webpack -g
```
`更新命令：cnpm install -g cnpm`