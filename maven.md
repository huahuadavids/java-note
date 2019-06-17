 # maven 

 ### install
 1. 下载解压到 /usr/local
 2. 配置bash
 ``` 
 touch ~/.bash_profile
 export M2_HOME = /usr/local/maven3（根据自己的路径地址设置）
 export PATH = $PATH:$M2_HOME/bin
 
 ```
 3. 配置 maven 阿里仓库
```
 // 在maven的程序目录下，conf目录下的settings.xml

 <mirrors>
    <mirror>
      <id>alimaven</id>
      <name>aliyun maven</name>
      <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
      <mirrorOf>central</mirrorOf>
    </mirror>
  </mirrors>
  
 // pom.xml 
 <repositories>
     <repository>
         <id>aLiYun</id>
         <url>https://maven.aliyun.com/repository/public</url>
         <releases>
             <enabled>true</enabled>
         </releases>
     </repository>
 </repositories>

```
4. 配置本地仓库地址 
``` 
 <localRepository>D:\MavenLibs</localRepository>

```
 
### Maven仓库
> Maven仓库用来存放Maven管理的所有Jar包。分为：本地仓库 和 中央仓库。

- 本地仓库：Maven本地的Jar包仓库。
- 中央仓库： Maven官方提供的远程仓库。
当项目编译时，Maven首先从本地仓库中寻找项目所需的Jar包，若本地仓库没有，再到Maven的中央仓库下载所需Jar包。

### 坐标 
> groupId(所需Jar包的项目名) 和 artifactId(所需Jar包的模块名) 构成了一个Jar包的坐标 

 ### POM
 - 是项目对象模型，pom.xml，类似package.json 
 - 项目生命周期 
 - 优势，1 是项目构建自动化，2 是依赖管理统一化  
 - jar包不在项目中， jar包在本地仓库中 ，同时还有版本的管理 
 
### 传递依赖 与 排除依赖
- 传递依赖：如果我们的项目引用了一个Jar包，而该Jar包又引用了其他Jar包，那么在默认情况下项目编译时，Maven会把直接引用和简洁引用的Jar包都下载到本地。
- 排除依赖：如果我们只想下载直接引用的Jar包，那么需要在pom.xml中做如下配置：(将需要排除的Jar包的坐标写在中)

``` 
<exclusions>
    <exclusion>
        <groupId>cn.missbe.web.search</groupId>
        <artifactId>resource-search</artifactId>
        <packaging>pom</packaging>
        <version>1.0-SNAPSHOT</version>
    </exclusion>
</exclusions>
```

### 依赖范围scope
> 在项目发布过程中，帮助决定哪些构件被包括进来。欲知详情请参考依赖机制。    
- compile ：默认范围，用于编译      
- provided：类似于编译，但支持你期待jdk或者容器提供，类似于classpath      
- runtime: 在执行时需要使用      
- test:    用于test任务时使用      
- system: 需要外在提供相应的元素。通过systemPath来取得      
- systemPath: 仅用于范围为system。提供相应的路径      
- optional:   当项目自身被依赖时，标注依赖是否传递。用于连续依赖时使用


### 聚合
> 将多个项目同时运行就称为聚合。只需在pom中作如下配置即可实现聚合
```
<modules>
    <module>web-connection-pool</module>
    <module>web-java-crawler</module>
</modules>
``` 

 ### ant
 > 只有项目构建，没有依赖管理 


 ### 生命周期
 - compile 编译， 编译为class
 - clean  清理 删除target的东西
 - install 打包并且部署到本地仓库 
  
 