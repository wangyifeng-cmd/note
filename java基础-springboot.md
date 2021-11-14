# JAVA基础---springboot

## 编译器：intellij IDEA

### 快捷键（我安装了vscode快捷键插件）

- 调出基本语句：ctrl+alt+t
- 提示：ctrl+alt+space(空格)
  - 我另外加了alt+/

- 选中这个词：alt+shift+向右箭头

- 格式化文档：alt+shift+f
  - 我另外加了alt+q

- 取消撤销：ctrl+shift+z
  - 我另外加了ctrl+y

- 删除这一行：ctrl+x



### 快捷语句

- psvm：main函数

- sout：System.out.println

- fori：for循环



### 异常处理：try{} catch{} finally{}

```java
try {
    return 0;//需要测试的代码
} catch (Exception e) {
    e.printStackTrace();//如果测试的代码出错，就会再catch中返回错误
} finally {
     //这里的代码无论测试的代码是否出错都会执行
}
```

### String的常用方法Ⅰ

- length()
  返回当前字符串的长度

- index0f(int ch)
  查找ch字符在该字符串中第-次出现的位置

- index0f(String str)
  查找s tr子字符串在该字符串中第-次出现的位置

- lastIndex0f(int ch) 
  查找ch字符在该字符串中最后-次出现的位置

- lastIndex0f(String str)
  查找str子字符串在该字符串中最后- -次出现的位置

- substring (int beginIndex)
  获取从beginIndex位置开始到结束的子字符串

- substring (int beginIndex, int endIndex) 获取从beginIndex位置开始到endIndex位置的子字符串

- trim()
  返回去除了前后空格的字符串

- equals(0bject obj)
  将该字符串与指定对象比较,返回true或false

- toLowerCase ()
  将字符串转换为小写

- toUpperCase()
  将字符串转换为大写

- charAt (int index)
  获取字符串中指定位置的字符

- split(String regex, int limit)

  将字符串分割为子字符串，返回字符串数组

- getBytes ()
  将该字符串转换为byte数组

### String的常用方法Ⅱ

- 字符.toLowerCase()

  转换为小写

- 字符.charAt(1)

  获取索引为1的字符

- 字符.getBytes()

  //将字符串转换为byte[]，并打印输出

  byte[] b = str.getBytes();

- 字符.equals()

  //判断内容相同，地址可以不相同

  第一个字符.equals(第二个字符)

  //判断地址相同

  第一个字符 == 第二个字符

### 包装类

| 基本类型 | 对应的包装类 |
| :------: | :----------: |
|   byte   |     Byte     |
|   shot   |    Short     |
|   int    |   Integer    |
|   long   |     Long     |
|  float   |    Float     |
|  double  |    Double    |
|   char   |  Character   |
| boolean  |   Boolean    |

```java
public class HelloWorld {
    public static void main(String[] args) {
		// 定义int类型变量，值为86
		int score1 = 86; 
		// 创建Integer包装类对象，表示变量score1的值
		Integer score2=new Integer(score1);
		// 将Integer包装类转换为double类型
		double score3=score2.doubleValue();
		// 将Integer包装类转换为float类型
		float score4=score2.floatValue();
		// 将Integer包装类转换为int类型
		int score5 =score2.intValue();
		System.out.println("Integer包装类：" + score2);
		System.out.println("double类型：" + score3);
		System.out.println("float类型：" + score4);
		System.out.println("int类型：" + score5);
	}
}
```

### 自动装箱 + 手动装箱  ||  自动拆箱 + 手动拆箱

```java
public class HelloWorld {
    public static void main(String[] args) {
         
        // 定义double类型变量
		double i = 91.5;
         // 手动装箱
		Double x =  new Double(i);
        // 自动装箱
		Double y =  i;
        System.out.println("装箱后的结果为：" + x + "和" + y);
         
        // 定义一个Double包装类对象，值为8
		Double j = new Double(87.0);
        // 手动拆箱
		double a =  j.intValue();
        // 自动拆箱
		double b =  j;
         System.out.println("拆箱后的结果为：" + a + "和" + b);
         
	}
}
```

### 基本类型和字符串之间的转换

```java
public class HelloWorld {
    public static void main(String[] args) {
         
        //将基本类型转换为字符串
        int a = 10;
        String str1 = Integer.toString(a);//方法一
        String str2 = String.valueOf(a);//方法二
        String str3 = a + "";//方法三
        System.out.println(str1 + str2 + str3);//101010
        
        //把字符串转换为基本类型
        String str = "8";
        int b = Integer.parseInt(str);//方法一
        int c = Integer.valueOf(str);//方法二
        System.out.println(b + "" + c);//88
         
	}
}
```

### 第一种方法：从系统获取日期

- Date d = new Date();
- format() 方法将日期转换为指定格式的文本
- parse() 方法将文本转换为日期

```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class HelloWorld {
    
    public static void main(String[] args) throws ParseException {
        
		// 使用format()方法将日期转换为指定格式的文本
		SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy年MM月dd日 HH时mm分ss秒");
		SimpleDateFormat sdf2 = new SimpleDateFormat("yyyy/MM/dd HH:mm");
		SimpleDateFormat sdf3 = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        
		// 创建Date对象，表示当前时间
        Date now = new Date();
        
        // 调用format()方法，将日期转换为字符串并输出
		System.out.println(sdf1.format(now));
		System.out.println(sdf2.format(now));
		System.out.println(sdf3.format(now));

		// 使用parse()方法将文本转换为日期
		String d = "2014-6-1 21:05:36";
		SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        
         // 调用parse()方法，将字符串转换为日期
		Date date = sdf.parse(d);
        
		System.out.println(date);
	}
}
```

### 第二种方法：从系统获取日期

- Calendar c = Calendar.getInstance();

```java
import java.util.Calendar;

public class calender {

    public static void main(String[] args) {
        Calendar c = Calendar.getInstance();//创建Canlendar对象
        int year = c.get(Calendar.YEAR); //获取年
        int month = c.get(Calendar.MONTH) + 1; //获取月份，0表示1月份
        int day = c.get(Calendar.DAY_OF_MONTH); //获取日期
        int hour = c.get(Calendar.HOUR_OF_DAY); //获取小时
        int minute = c.get(Calendar.MINUTE); //获取分钟
        int second = c.get(Calendar.SECOND); //获取秒
        System.out.println("当前时间:" + year + "-" + month + "-" + day + "-" + hour + "-" + minute + ":" + second);
    }
}
```

- getTime() --- Date date = c.getTime(); //将Calendar对象转换为Date对象
- getTimeInMillis() --- 获取当前毫秒数

```java
Date date = c.getTime(); //将Calendar对象转换为Date对象
Long time = c.getTimeInMillis(); //获取当前毫秒数
System.out.println("当前时间: " + date);
System.out.print1n( "当前毫秒数: " + time) ;
```

### Math方法

| 返回值 |  方法名  |          返回的值           |
| :----: | :------: | :-------------------------: |
|  long  | round()  |          四舍五入           |
| double | floor()  |     小于参数的最大整数      |
| double |  ceil()  |     大于参数的最小整数      |
| double | random() | 返回[0,1)之间的随机数浮点数 |

