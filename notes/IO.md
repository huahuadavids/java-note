1. 输入流是读的
2. 流是单向的
3. 输出流是写的
4. 节点流(低级流)，可以从或者向一个特定的节点读写数据
5. 处理流（高级流），对一个已存在的流的处理和封装
6. InputStream是输入流的父类，Outputstream是输出流的父类
7. ### java.io.FileOutputStream(file,isAdd) 
> 文件不存在自动创建文件,默认全部覆盖重新写,第二个参数就是追加 \r\n 是换行
```
File file = new File("."+File.separator + "demo.txt");
FileOutputStream fos = new FileOutputStream(file);
String str = "huahuaa/n哈哈哈";
byte[] data = str.getBytes("utf-8");
fos.write(data);
fos.close();
```
8. ### java.io.FileInputStream(file,isAdd) 
> 从文件读内容
```
File file = new File("."+File.separator + "debug" + ".txt");
FileInputStream fis = new FileInputStream(file);

byte[] data = new byte[100];

int len = fis.read(data);

String str = new String(data,0, len, "utf-8");

```