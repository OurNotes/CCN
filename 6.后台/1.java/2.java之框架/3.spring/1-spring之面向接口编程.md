操作总流程：
- 1、创建接口
- 2、创建实现类
- 3、创建主函数输出数据

----------

项目结构：

![](image/1-1.png)
代码结构：

![](image/1-2.png)
# 接口的代码
```
package com.persion.test;

public interface TestOnce {
	String once(String once);
}
```
# 实现类的代码
```
package com.persion.test;

public class TestOnceImpl implements TestOnce{

	@Override
	public String once(String once) {
		
		return "你好"+once;
	}

}
```
# 主函数代
```
package com.persion.test;

public class Test {
	public static void main(String[] args) {
		TestOnce TO=new TestOnceImpl();
		System.out.println(TO.once("丽丽"));
	}
}
```