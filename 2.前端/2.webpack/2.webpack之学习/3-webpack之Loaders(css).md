总操作步骤：
- 1、下载安装处理样式表工具
- 2、在app文件夹添加css文件
- 3、修改main.js文件

[![](https://img.shields.io/badge/源代码-WebpackProjects--Loaders--css-blue.svg "源代码 WebpackProjects-Loaders-css")](https://github.com/lidekai/WebpackProjects-Loaders-css.git)

----------

# 下载安装处理样式表工具(在项目里添加)
```
cnpm install --save-dev css-loader style-loader
```
# 在app文件夹添加css文件
```
/**
 * main.css
 */
body{
	background-color: red;
}
```
# 修改main.js文件
```
//main.js
require("./main.css");
const greeter = require('./Greeter.js');
document.write(greeter());
```