### 随机数
1. java.lang.math
```
Math.random()//0 - 1之间的小数

```
2. java.util.random
```
Random(long seed)：使用单个 long 种子创建一个新的随机数生成器。
Random ran = new Random();
ran.nextInt(100);

```

### Array和Arrays collection和collections 
> Array就是数组，也就是长度固定的容器，一但创建了这个对象就不能改变其大小(capacity)。Arrays是Array的工具类，其静态方法定义了对Array的各种操作 
```
int as = Arrays.binarySearch(arr, "one");
		System.out.println(as);
		
```
# collection
> collection接口实现了iterator接口
## 1. List
### collections.sort() //list排序
> //要实现比较，必须实现一个接口comparable
```
class Point implements Comparable<Point> {
	private int x ;
	private int y;
	public Point() {
		this.x = 1;
		this.y = 1;
	}
	public Point(int x,int y) {
		this.x = x;
		this.y = y;
	}
	public int getX() {
		return x;
	}
	public void setX(int x) {
		this.x = x;
	}
	public int getY() {
		return y;
	}
	public void setY(int y) {
		this.y = y;
	}
	public String toString() {
		return ("x="+x+"&y="+y);
	}
	@Override
	public int compareTo(Point p) {
		return   (this.x * this.x + this.y*this.y) - (p.x*p.x+p.y*p.y);
	}
}
List<Point>	list = new ArrayList<Point>();
list.add(new Point(1,2));
list.add(new Point(1111,2222));
list.add(new Point(11,12));
list.add(new Point(21,22));
list.add(new Point(111,222));
System.out.println(list);
Collections.sort(list);
System.out.println(list);

```
### 自定义比较器
```
// 如果想多次用，创建自定义的比较器
class myComp implements Comparator<String> {
	@Override
	public int compare(String a, String b) {
		return a.length() - b.length();
	}
}
// 如果用一次
Comparator<String> com1 = new Comparator<String>() {
	public int compare(String a, String b) {
		return a.length() - b.length();
	}
};

List<String> strList = new ArrayList<String>();
strList.add("花花");
strList.add("三国演义");
strList.add("西游记");
System.out.println(strList);
myComp com = new myComp();
Collections.sort(strList,com);
System.out.println(strList);


```

### toArray collection转化为数组 

```
    Collection<String> list = new ArrayList<String>();
for(int a =0;a<5;a++) {
	list.add(String.valueOf(a));
}
System.out.println(list);

String arr[] = list.toArray(new String[list.size()]);//size大了，多的就是null，少了也能用
System.out.println("arr length = " + arr.length);
for(String a:arr) {
	System.out.println(a);
}

```

### 数组转集合 只能转List，set不能放重复元素
```
String arr[] = {
		"one","two","three","four"
};
List<String> list = Arrays.asList(arr);
System.out.println(list);
list.add("fice");//报错 数组和集合相同地址
List<String> list1 = new ArrayList<String>();
list1.addAll(list);		

//可以这么写
List<String> list1 = new ArrayList<String>(list);

list1.add("five");
System.out.println(list1);

```

### 集合存放元素的引用
- list 可重复而且有序 数组实现  查询快
- set 不可以重复无序 链表实现 增删快
- List是一个接口，而ListArray是一个类。 
ListArray继承并实现了List。


1. ## list类型的
- ==arraylist类(用的多一些)==
- linkedlist类
- vector类
- stack类
- ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构。
- 创建了一个向量类的对象后，可以往其中随意插入不同类的对象，即不需顾及类型也不需预先选定向量的容量，并可以方便地进行查找
-  ArrayList会比Vector快，他是非同步的，如果设计涉及到多线程，还是用Vector比较好一些,Vector是一种老的动态数组，是线程同步的，效率很低，一般不赞成使用
2. ## set类型的
- hashSet
- treeSet
- queue结构集合
- queue接口
---
1. ### arrayList 
> contains 方法，比如的是类的equals函数
```
import java.util.*;
ArrayList list1 =new ArrayList();
Stuff s1 = new Stuff("bill",22,1222.22);
list1.add(s1);//返回一个布尔值
list1.add(s1);//可以有一样的元素
list1.add(0，s1);//可以指定在具体位置插入
System.out.println("list1的长度是"+list1.size());
System.out.println("list1包含s1："+list1.contains(s1));
Stuff tmp = (Stuff)list1.get(0);
System.out.println("list1的第一个人的名字是"+tmp.name);
list1.remove(0);//可以删除索引，可以删除对象,只是删除一个元素
list1.clear(); //清空list
System.out.println("list1的长度是"+list1.size());

```
#### subList 
```
List<String> list = new ArrayList<String>();
for(int a =0;a<5;a++) {
	list.add(String.valueOf(a));
}
System.out.println(list);
List<String> subList = list.subList(0,2);
System.out.println(subList);
subList.set(0,"11111");//对子集的修改，父集也受影响

List.subList(0,3).clear();//删除一个子集


```		

2. ### LinkedList （addFirst addLast removeFirst removeLast ）
> LinkedList可以在前边add和后边add，add（index，object）
3. ### vector

## 集合操作
1. ### 并集
```
Collection c1 = new ArrayList();
c1.add("apple");
c1.add("mi");
c1.add("vivo");
System.out.println(c1);

Collection c2 = new HashSet();//顺序不对
c2.add("黑莓");
c2.add("三星");
c2.add("三星");
System.out.println(c2);

c1.addAll(c2);

System.out.println(c1);
```
2. ### 去差集
> 两个集合相同的元素删掉
```
c1.removeAll(c2);

System.out.println(c1);
```		

