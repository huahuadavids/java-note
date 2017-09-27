## 安卓install资源网址
http://tools.android-studio.org/index.php/sdk/


### 安装JDK
- #### path是为了让exe文件可以在任意目录下运行
- #### classpath是为了让class文件可以在任意目录下运行
1. 系统环境变量 JAVA_HOME
```
C:\Program Files\Java\jdk1.8.0_144

```
2. 系统环境变量 path 
```
 %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
 ```
3. 系统环境变量 classpath
 ```
 .;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar
 ```
4. cmd

```
java -version

```