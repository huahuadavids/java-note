 # maven 
 
 ### install
 1. 下载解压到 /usr/local
 2. 配置bash
 ``` 
 touch ~/.bash_profile
 export M2_HOME = /usr/local/maven3（根据自己的路径地址设置）
 export PATH = $PATH:$M2_HOME/bin
 
 ```
 3 配置 maven 阿里仓库
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
 
 
 ### POM
 - 是项目对象模型，pom.xml，类似package.json 
 - 项目生命周期 
 - 优势，1 是项目构建自动化，2 是依赖管理统一化  
 - jar包不在项目中， jar包在本地仓库中 ，同时还有版本的管理 
 
 ### ant
 > 只有项目构建，没有依赖管理 

 ### 新建maven项目
 - file new maven
 - 勾选 Create from archetype 
 - 选择 maven-archetype-quickstart(普通项目)/maven-archetype-webapp(web项目) 

 
 