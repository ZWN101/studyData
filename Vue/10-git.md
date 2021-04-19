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

