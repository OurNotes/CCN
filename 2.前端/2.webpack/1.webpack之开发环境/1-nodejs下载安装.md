操作总流程：
- 1、[下载安装node.js](#node.js-01)
- 2、[配置node.js环境](#node.js-02)
- 4、[安装淘宝 NPM 镜像](#node.js-03)
- 5、[配置安装淘宝 NPM 镜像环境](#node.js-04)
- 6、[使用 cnpm 安装 webpack](#node.js-05)


----------
# <a name="node.js-01" href="#" >下载安装node.js</a>
[![](https://img.shields.io/badge/官网-Node.js-red.svg "官网 Node.js")](https://nodejs.org/en/)

> 在doc下测试node.js是否成功
```shell
node --version
```

# <a name="node.js-02" href="#" >配置node.js环境</a>

> 将Nodejs安装路径添加到Path路径后面
在path添加node.js的路径：C:\Software\nodejs

>cmd中键入两行命令
```
npm config set prefix "C:\Software\nodejs\node_global"

npm config set cache "C:\Software\nodejs\node_cache"
```
>配置path
```
NODE_PATH:C:\Software\nodejs\node_global\node_modules

在path添加：;%NODE_PATH%;C:\Software\nodejs\node_global

```

# <a name="node.js-03" href="#" >安装淘宝 NPM 镜像</a>
```shell
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

`更新命令：cnpm install -g cnpm`

> 在doc下测试cnpm是否成功
```shell
cnpm --version
```

# <a name="node.js-04" href="#" >配置安装淘宝 NPM 镜像环境</a>

> 将Nodejs安装路径添加到Path路径后面

在path添加cnpm的路径：C:\Software\nodejs\node_global


# <a name="node.js-05" href="#" >使用 cnpm 安装 webpack</a>
```shell
cnpm install webpack -g
```
