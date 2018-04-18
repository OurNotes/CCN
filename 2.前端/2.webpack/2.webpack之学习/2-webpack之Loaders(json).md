总操作流程：
- 1、下载安装Loaders
- 2、在app文件夹创建config.json文件
- 3、修改Greeter.js文件
- 4、修改main.js文件

[源码](https://github.com/lidekai/WebpackProjects-Loaders-json.git)

----------

![](image/2-1.png)

# 下载安装Loaders
```
cnpm install -g --save-dev json-loader
```
# 在app文件夹创建config.json文件
```
{
    "greetText": "Hi there and greetings from Json!"
}
```

# 修改Greeter.js文件
```
// Greeter.js
var config = require('./config.json');

module.exports = function() {
  var a = config.greetText;
  return a;
};
```

# 修改main.js文件
```
//main.js
const greeter = require('./Greeter.js');
document.write(greeter());
```

`
注：件由于webpack3.*/webpack2.*已经内置可处理JSON文件，这里我们无需再添加webpack1.*需要的json-loader。
`
不需要加
![](image/2-2.png)