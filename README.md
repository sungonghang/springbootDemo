
## spring多环境配置
   在applicaiton.yml中spring -- profiles --active:test中配置需要激活的环境配置项 \
设置环境
* 1.启动jar包时设置spring.profiles.active
    > java -jar xxx.jar --spring.profiles.active=test
* 2.maven打包时设置环境
    > mvn clean package -Dspring.profiles.active=test \
      mvn clean package -Ptest 
      
 注意需要在pom文件中声明profiles标签，在application.yml中要定义\@属性名\@的引用, maven多profile打包下  -P -D -U ,P代表在\<profiles> 指定的\<id>中，
 可以通过-P进行传递或赋值
  ```
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
 ``` 
 D代表（Properties属性）
 ```
<properties>
  <attr>defaultattr</attr>
</properties>
```
执行mvn -Dattr=newattr clean package，则pom.xml内attr的实际值将被替换成newattr。 \
U代表update，强制刷新本地仓库不存在release版和所有的snapshots版本。
* 对于release版本，本地已经存在则不会重复下载。
* 对于snapshots版本，不管本地是否存在，都会强制刷新，但是刷新并不意味着把jar重新下载一遍，只下载几个比较小的文件，通过这几个小文件确定本地和远程仓库的版本是否一致，再决定是  否下载 \
mvn clean install -e -U   -e详细异常,-U强制更新
## git命令
### git的相关操作
 * 1.查看相关的配置 `git config --list`
 * 2.设置全局用户名 `git config --global user.name ***`
 * 3.设置全局email  `git config --global user.email ***`
 * 4.生成公钥  `ssh-keygen -t rsa -C "邮箱"`
 * 5.测试连通性 `ssh -T git@github.com` 
### git将本地项目推送到远程仓库
 * 1.将本地项目初始化`git init` 
 * 2.将代码放置暂存区`git add .`
 * 3.将暂存区放置本地仓库`git commit -m "**"`
 * 4.与远程分支建立连接 `git remote add origin  git@github.com:sungonghang/springbootDemo.git`
 * 5.将代码推送到远程仓库 `git push -u origin master` \
 注意在将代码推送到远程仓库的时候，如果在创建仓库的时候有README文件，推送时会报错failed to push some refs to https://github.com/ghsun/TEST.git,这是因为新创建的那个仓库里面的README文件不在本地仓库目录中，这时可以通过以下命令先将内容合并以下：`git pull --rebase origin master`
### 将文件添加到暂存区
```
git add <文件.后缀>
git add <文件1.后缀 文件2.后缀>
git add .   /*所有文件*/  将文件的修改、文件的新建，添加到暂存区
git add -A  /*所有文件*/  将文件的修改，文件的新建、文件的删除，添加到暂存区
git add -u  /*所有文件*/  将文件的修改、文件额删除,添加到暂存区
git add --all  /*所有文件*/
```
### 提交暂存区文件到本地库
 ```
 git commit -m"提交说明" <文件.后缀>
 git commit -m"提交说明"  /*提交暂存区所有文件*/
 ```
### 查看本地库日志文件
```
git log 查看详情的日志
git log --oneline 查看简介的日志 简介的索引值
git log --pretty=oneline 查看简介日志 完成的索引值
```
### 版本回退
```
git reset --hard <索引值>
git reset --hard HEAD^ /* 一个^代表后退一步，有几个就代表后退几步，只能后退*/
git reset --hard HEAD~<步数> /*根据步数后退，只能后退*/
git push -f 强制推送,将远程仓库进行覆盖
```
### 分支操作
```
git branch 查看本地分支
git branch -r 查看远程分支
git branch -a 查看全部分支
git branch branch1  新建分支branch1
git checkout -b branch1 新建分支branch1，并切换到分支branch1
git push --set-upstream origin dev 将本地的div分支推送到远程
git push --set-upstream origin beta 将本地beta分支推送到远程
git pull origin master 拉取远程master分支到本地
git merge dev 将dev分支合并到master分支
git push origin master 将本地更新后的master合并到远程
git branch -d dev 删除本地dev分支
git push origin --delete dev 删除远程dev分支
```
### git版本发布
```
git tag -a <tagname> -m "add description release notes " #创建标签
git tag -l #查看标签
git tag -d <tagname> #删除标签
git push origin <tagname> #推送一个本地标签到远程仓库
git push origin --tags #推送全部未推送过的本地标签
git push origin :refs/tags/<tagname> #删除远程便签
```





      


       


