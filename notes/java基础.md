### cpu处理快，从内存取数据块，因为都是电信号，硬盘就是磁盘，先读到内存再到cpu
### java se 桌面开发 javase是基础,
### java ee web开发

### java技术简述
- java oop
- java gui
- java 数据库
- java 文件I/O
- java 网络编程
- java 多线程

### JDK
1. jre java runtime envirorment
2. 工具包 java编译器javac.exe，java解释执行器java.exe
3. java 类库

### javadoc 自动按照注释生成文档
## notes

- javac 编译hello.java为hello.class 
- java加载到java.class到 JVM 执行
- 和c语言一样，变量越界 long = int + int可以
## java的进制
```
int a = 0x11; // 十六进制
int b = 012; //八进制
```		
### 数据类型 int 和c语言一致的

```
byte a1 = 11;
short b1 = 11;
int a = 100;
int c = 100;
long b = a + c;
	
```
- char两个字节，可以放汉字
- 汉字是unicode码，数字字符是aschii码 
- 数据类型，低精度可以转高精度，反之不行,和c语言一样
- 字符串转化为float和类型强制转换
```
int a = (int)1.2; 
String aa = '12';
float f1 = Float.parsefloat(aa)//字符串转化为float
int a = Integer.parseInt("11")//字符串转int

```
- 默认小数是double类型的 所以float 要加f

- 3 + 3.4F + 3.5 是double 

- java拼接字符串是用 + 

- 常量命名也是大写

## 包
- 包名小写
- 用 点 分层

## 数组
```
int b[] = new int[6]; //定义6个数组

iny c[] = {
    1,2,3,4
}

```

### 多维数组
```
int aa[][] = new int[2][3];
int ar[][] = {
		new int[2],
		new int[3]
};

```
### 比较字符串 相等 用 equals不是 == 
> == 比较的是地址，equals是内容
## 泛型
> 泛型的要求必须是引用类型,本质上就是object

```
Point<Integer> p1 = 
		new Point<Integer>(1,2);
p1.setX(1);//可以传入基本类型，因为会自动装箱
System.out.println(p1.getX());
System.out.println(p1.getClass());

Point p2 = p1;// p2默认传入的就是Object类型的
p2.setX("111");

```

## 包装类，把基本类型包装成object 

基本类型 | 包装类型 | 父类
---|---|---
int  | java.lang.Interger | java.lang.Number
char | java.lang.Chracter | java.lang.Object

## 基本类型转包装类
```
Integer in1 = new Integer(1);
Integer in2 = Integer.valueOf(1);//推荐这个

int a = in1.intValue(); //转为整数

```

### 最大值和最小值
```
int max = Integer.MAX_VALUE;
int min = Integer.MIN_VALUE;
System.out.println(max);	
System.out.println(min);

```	
### 字符串转基本类型 type.parseType 
```
Double.parseDouble(s)

```
### jdk1.5 自动拆装箱
> 编译器认可，而不是jvm认可，编译器自动转换
```
Integer aa = 11;

int a =new Integer(10);

```