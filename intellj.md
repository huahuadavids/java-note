# intellj
- 是以项目作为工作空间，
- 自带maven 
- 直接创建java项目的方式不推荐
- 设置了jdk同时也要设置编译版本的jdk版本
``` 
// 设置项目 jdk版本 
// 点击右上角 project structure
// 点击project 和 module设置

// 设置编译版本  
// 点击preference
// 选择build，excution deployment 
// compiler => java compiler 

``` 
- 设置编码
``` 
 // 点击preference
 
 // editor 
 
 // file encodings 

```

 ### 新建maven项目
 - file new maven
 - 勾选 Create from archetype 
 - 选择 maven-archetype-quickstart(普通项目)/maven-archetype-webapp(web项目) 
 - 选择maven路径和配置文件地址
 - 开启maven自动导包，build、execution、employment中的builds tools的maven 

 ### 关联maven(不是创建项目方式)
 - file -> settings -> maven 