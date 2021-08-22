```
echo "# gittest" >> README.md
git init //初始化项目（一次性把所有的项目放在：VSCode：更改）
git add README.md  //提交到暂存区（VSCode：暂存的更改）
git commit -m "first commit" //把暂存区的文件提交到本地
git branch -M main
git remote add origin https://github.com/ZWN101/gittest.git //与远程仓库建立连接
git push -u origin main //把项目提交到远程仓库
```

```
git clone 仓库连接 //把Git上的项目克隆到本地
git add . //把所有的变化提交到暂存区
git commit -m ''  从暂存区提交到本地
git status //查看当前的状态，查询暂存区里已修改的文件（暂存的更改）
```

### 常用命令

```
git log --查看提交记录 打印出所有的提交记录
git show commitId --查看某一条提交记录的详情
git show commitId fileName --查看某次commit提交中某个文件的修改
git status --查看哪些修改被暂存到了缓存区，哪些没有
git clone git://github.com/jquery/jquery.git --克隆远程仓库到本地
git remote add [remoteName][url] --与远程仓库建立连接
git add . --将所有已修改的文件提交到暂存区
git commit -m '' --从暂存区提交到本地
git push [remoteName][localBranchName] --推送远程仓库
git pull [remoteName][localBranchName] --拉取远程仓库

git push origin(远程仓库的名字) osp-1226(远程仓库的某一分支)
git pull origin(远程仓库的名字) osp-1266(拉取远程仓库的osp分支的代码到本地)
```

#### git status

![image-20210502221536760](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210502221536760.png)

```
git branch iss58 --创建新的分支iss58
git checkout master --切换到master分支（如果master）
git checkout -b iss58 --创建新的分支iss58并切换
git branch -d iss58 --删除iss58分支
git merge iss58 --将iss58分支合并到当前分支
git fetch origin feature-osp-1239 拉取远程feature-osp-1239分支
```

* 发布项目用的分支 master
* 开发项目用的分支 develop
* 每新增一个功能或者修复某个bug，在develop的分支的基础上新增一个分支进行开发，开发完成之后，到develop分支进行合并merge

内网和外网

```
git remote add local http://47.100.186.110:6032/root/nchinalife-front.git 具体意义
```

```
存储当前更改到本地
git stash 
git stash save '注释'
git stash list
git stash show@{序号}
git stash apply@{序号} 应用某个stash,但不会把这个stash从stash list中清除掉
git stash pop@{序号} 应用某个stash,会把这个stash从stash list中清除掉
git stash clear 
git stash drop@stash{序号} 删除某次
花括号使用转义字符`
```



路由的两种模式的区别

模块化开发 ES6 和commonJS的区别

双向绑定原理

全双工通信