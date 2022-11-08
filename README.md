## 清元多链 QYmeta Java SDK

清元多链QYmeta Java是针对国内多家联盟链提供的一套完整的web3、数字藏品等解决方案的java sdk版。开发者无需深入了解各联盟链的相关技术知识，可通过QYmeta java SDK 快速搭建自己的web3、数字藏品应用。

* 清元多链 [官网](http://openqkl.newmin.cn/)

* 清元链 NFT SDK [文档](https://github.com/qymeta/qymeta_java/blob/main/doc/qymeta_java.md)

### Installation

下载sdk的jar包

### 将sdk加入maven
```
mvn install:install-file -DgroupId=art.qymeta -DartifactId=qymeta-java-sdk -Dversion=1.0.0 -Dpackaging=jar -Dfile=你的jar包的绝对路径【qymeta-java.jar】
```
### 引入sdk依赖
```
        <dependency>
            <groupId>art.qymeta</groupId>
            <artifactId>qymeta-java-sdk</artifactId>
            <version>1.0.0</version>
        </dependency>
```
### Change Logs
#### 0.0.2 2022/11/01
* 清元链 NFT 相关接口发布

