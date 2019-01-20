总操作流程：
- 1、下载安装饿了么组件
- 2、项目中引用
- 3、看效果
 
 # 下载安装饿了么组件
> 1、创建vue项目后，开启的服务器，要退出

```
快捷键：Ctrl+C
```

>2、在项目文件路径下进行命令，将组件安装到项目中

 ```
 cnpm i element-ui --save
 ```

 - 成功标志

![](image/6-1.png)


 # 项目中引用

 >在main.js中引用，在App上导入

 ![](image/6-2.png)

 ```
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
 ```

 ```
 Vue.use(ElementUI)
 ```

 # 看效果

> 1、写入组件代码

> 2、运行项目
```
cnpm run dev
```

> 3、浏览器进入：http://localhost:8080看效果

