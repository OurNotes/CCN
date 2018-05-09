[参看视频](https://www.imooc.com/video/2803)
```
import java.net.InetAddress;
import java.net.UnknownHostException;
import java.util.Arrays;

/*
 * InetAddress类
 */
public class Test01 {

	public static void main(String[] args) throws UnknownHostException {
		// 获取本机的InetAddress实例
		InetAddress address = InetAddress.getLocalHost();
		System.out.println("计算名：" + address.getHostName());
		System.out.println("IP地址：" + address.getHostAddress());
		byte[] bytes = address.getAddress();// 获取字节数组形式的IP地址
		System.out.println("字节数组形式的IP：" + Arrays.toString(bytes));
		System.out.println(address);// 直接输出InetAddress对象

		// 根据机器名获取InetAddress实例
		// InetAddress address2=InetAddress.getByName("laurenyang");
		InetAddress address2 = InetAddress.getByName("1.1.1.10");
		System.out.println("计算名：" + address2.getHostName());
		System.out.println("IP地址：" + address2.getHostAddress());
	}

```