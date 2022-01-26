#springbootDemo
spring 多环境配置
主要配置 ：在applicaiton.yml中spring -- profiles --active:text中配置需要激活的环境配置项
设置环境
1.启动jar包时设置spring.profiles.active
java -jar xxx.jar --spring.profiles.active=test
2.maven打包时设置环境
mvn clean package -Dspring.profiles.active=test
mvn clean package -Ptest 注意需要在在pom文件中生命profiles标签 在 application.yml
中要定义@属性名@的引用
maven多profile打包下  -P -D -U
P代表（profiles配置文件）
在<profiles> 指定的<id>中，可以通过-P进行传递或赋值
<profiles>
<profile>
<id>prod</id>
...
</profile>
<profile>
<id>test</id>
...
</profile>
</profiles>
D代表（Properties属性）
<properties>
<attr>defaultattr</attr>
</properties>
执行mvn -Dattr=newattr clean package，则pom.xml内attr的实际值将被替换成newattr

U代表update
强制刷新本地仓库不存在release版和所有的snapshots版本
*对于release版本，本地已经存在则不会重复下载
*对于snapshots版本，不管本地是否存在，都会强制刷新，但是刷新并不意味着把jar重新下载一遍。
只下载几个比较小的文件，通过这几个小文件确定本地和远程仓库的版本是否一致，再决定是否下载
mvn clean install -e -U   -e详细异常,-U强制更新


git的相关操作
1.查看相关的配置  git config --list
2.设置全局用户名 git config --global user.name ***
3.设置全局email git config --global user.email ***
4.生成公钥 ssh-keygen -t rsa -C "邮箱"
5.测试连通性 ssh -T git@github.com 

      


       


