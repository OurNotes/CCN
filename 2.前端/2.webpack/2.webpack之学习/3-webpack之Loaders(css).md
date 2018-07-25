总操作步骤：
- 1、[下载安装处理样式表工具](#webpack-01)
- 2、[在app文件夹添加css文件](#webpack-02)
- 3、[修改main.js文件](#webpack-03)

[![](https://img.shields.io/badge/源代码-WebpackProjects--Loaders--css-blue.svg "源代码 WebpackProjects-Loaders-css")](https://github.com/lidekai/WebpackProjects-Loaders-css.git)

----------

# <a name="webpack-01" href="#" >下载安装处理样式表工具(在项目里添加)</a>
```
cnpm install --save-dev css-loader style-loader
```
# <a name="webpack-02" href="#" >在app文件夹添加css文件</a>
```
/**
 * main.css
 */
body{
	background-color: red;
}
```
# <a name="webpack-03" href="#" >修改main.js文件</a>
```
//main.js
require("./main.css");
const greeter = require('./Greeter.js');
document.write(greeter());
```