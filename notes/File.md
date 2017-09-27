### java.io.file
- 访问文件的属性
- new or delete 文件或者目录
- 访问目录中的内容
- 不可以读取文件数据
```
// java中最好使用相对路径，因为linux没有盘符划分
//.表示项目所在目录	
File file = new File("."+File.separator+"demo.txt");
String fileName = file.getName();
System.out.println(fileName);//文件名

boolean exists = file.exists();//文件是否存在
System.out.println("file存在:"+exists);//文件名);//文件名


long fileSize = file.length();// 文件大小
System.out.println(fileSize);
 
boolean isfile = file.isFile();
System.out.println("is file: "+ isfile);

boolean isDir = file.isDirectory();
System.out.println("is isDirectory: "+ isDir);

boolean isHid = file.isHidden();
System.out.println("is isHidden: "+ isHid);

//修改时间
long time = file.lastModified();
System.out.println(time);
Date date = new Date(time);
System.out.println(date);
SimpleDateFormat smf= new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
System.out.println(smf.format(date));

file.delete();//删掉文件
```
### 操作文件
> 创建文件要捕获异常
```
String myFile = "demo2.txt";//默认就是当前目录
File file = new File(myFile);
if(file.exists()) {
	System.out.println("文件已经存在");
	file.delete();
	System.out.println("文件删除完毕");
}else {
	file.createNewFile();
	System.out.println("文件创建完毕");
}
	
```
### 创建目录
> 创建多级目录使用mkdirs
```
String myFile = "demo2";//默认就是当前目录
File myDir = new File(myFile);
if(!myDir.exists()) {
	// mkdir 创建子目录需要父目录存在·
	if(myDir.mkdir()) {
		System.out.println("目录创建成功");
	}
}
```
### delete
> 删除文件夹比如为空才可以删除
```
File dir = new File("." + File.separator + "demo");
	
	if(dir.exists()) {
		File[] subs = dir.listFiles();
		if(subs.length > 0 ) {
			for(File f:subs) {
				System.out.print(f.isFile() ? "文件:":"文件夹" );
				System.out.println( f.getName());
			}
		}else {
			System.out.println("文件夹为空");
		}

	}

```
### 删除文件夹
> java删除不存在的文件不会报错
```
public static void main(String[] args) {
	File dir = new File("." + File.separator + "demo");
	delete(dir);

}
public static void delete(File file) {
	if(file.exists()) {
		if(file.isDirectory()) {
			File[] subs = file.listFiles();
			for(File f: subs) {
				delete(f);
			}
		}
		file.delete();
	}
}

```
### 重载的listFile方法
> 传入一个文件过滤器，返回符合条件的文件
```
File dir = new File(".");

File files[] = dir.listFiles(new FileFilter() {
	@Override
	public boolean accept(File file) {
		boolean strHead= file.getName().startsWith(".");
		boolean isDir = file.isDirectory();
		return strHead && isDir;
	}
	
});
for(File f:files) {
	System.out.println(f.getName());
}
```
## 读写数据 
> randomAccessFile(file,mode) 
可以自动创建文件，不可自动创建目录,基于指针操作的，随着指针的位置读写
- read 
```
int res = raf.read();// 读到-1表示读到末尾了

```
- write 
```
raf.write(97);// 写二进制，写一个int ,只写一个字节 8位
```

### 复制文件
> 复制的慢，因为内存到磁盘速度慢
```
RandomAccessFile src = new RandomAccessFile("./moun.ape","r");

RandomAccessFile dist = new RandomAccessFile("./music/hua.ape","rw");

int srcData = -1;
while((srcData = src.read() ) != -1) {
	dist.write(srcData);
}
System.out.println("copy ready");
src.close();
dist.close();

```
> 下边为优化 read重写方法
```
//read方法读取一个数组的byte时，最后一个小于数组的len，如果也写入，会有多的数据
RandomAccessFile src = new RandomAccessFile("./hua.jpeg","r");
RandomAccessFile dist = new RandomAccessFile("./dist/hua.jpeg","rw");
long startTime = System.currentTimeMillis();
byte[] buf = new byte[1024*10];//10k效率很高
int len = -1;
// 
while(  
	(len = src.read(buf) )!= -1
) {
	dist.write(buf,0,len);//读多少，写多少,从0开始写len个数据
}
long endTime = System.currentTimeMillis();
System.out.println("copy ready");
System.out.println(endTime - startTime);
src.close();
dist.close();
// 7656 initial 
// 3 

```
### raf操作文件指针和读取数据
```
/**
 * @description 向文件中写入int最大值
 */
int max = Integer.MAX_VALUE;
// raf.write(max);//write只能写int的低八位
raf.write(max >>> 24);
raf.write(max >>> 16);
raf.write(max >>> 8);
raf.write(max);

raf.writeInt(max);
raf.writeLong(1234L);

/**
 * @description获取指针位置
 */
p(raf.getFilePointer());// 17 int + int + long + 1 
raf.seek(0);
p(raf.getFilePointer());
int int1 = raf.readInt();
p(int1);
raf.close();

```
### 写入数据
> 写入字符串使用writeBytes
```
File file = new File("./person.dat");
RandomAccessFile raf = new RandomAccessFile(file, "rw");	
int a = 10;
while (a > 0) {
	raf.writeBytes("huahuadavids" + a + "                   ");//32
	raf.writeInt(a + 10);//4
	raf.writeInt(a + 4500);//4
	raf.writeUTF("2017-11-11");//10
	a--;
}
raf.close();
System.out.println("写入数据完毕");

```

### 综合练习
```
File file = new File("./emp.dat");
RandomAccessFile raf = new RandomAccessFile(file, "rw");
List<emp> empList = new ArrayList<emp>();
SimpleDateFormat smf = new SimpleDateFormat("yyyy-MM-dd");
for(int a = 0; a < 2;a++) {
	String name = getStr(32, raf);
	p(name);
	int age = raf.readInt();
	p(age);
	int wage = raf.readInt();
	String date = getStr(10, raf);
	Date dat = smf.parse(date);
	emp e = new emp(age,name,dat,wage);
	empList.add(e);
}	
raf.close();
p(empList.size());
```
