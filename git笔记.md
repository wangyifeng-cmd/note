## git命令行

### 下载git --- 官网地址

```html
https://git-scm.com/
```

### 把文件交给git管理

```bash
git init
```

### 本地配置名字和邮箱，相当于注册账号密码
```bash
git config --global user.name "wyf"
git config --global user.email "wangyifeng668@qq.com"
```

### 生成密钥

```bash
ssh-keygen -t -rsa -C"wangyifeng668@qq.com"
```

### 复制刚才生成的ssh key

```bash
clip < -/c/Users/nnf/.ssh/id_rsa.pub
```

### 如果出现"unkown key type -rsa"就输入

```bash
ssh-keygen -t -rsa就好了
```

### 回到GitHub

```bash
settings -> SSH and GpG keys -> 填写title和key值(~/ssh/id_rsa.pub)
```

### 连接远程仓库

```bash
git remote add origin + ssh地址
```

### 首次提交必须进行过一次提交

```bash
git push --set-upstream origin master
```

### 平时提交

```bash
#本地区->暂存区
git add 文件名 #提交单个文件
git add . #提交全部内容

#暂存区->历史记录区
git commit -m "王译锋的第一次提交"

#历史记录区->提交到gitHub上
git push
```

### 查看当前仓库的状态，看看内容有没有被修改过

```bash
git status
```

### 查看每次的改变

```bash
git diff
```

### 删除文件

```bash
rm 文件名
```

### 后悔药

```bash
git checkout -- .
```

### 查看commit的记录

```bash
git log#输入字母Q自动退出
```

```bash
git reflog（简洁版，查看版本号）
```

### 回到以前的版本

```bash
git reset --hard 版本号
```

### 从git上拉代码

```bash
git clone 仓库的ssh
```

### 删除之前的提交

```bash
git reset --hard HEAD^
#HEAD是指向最新的提交，上一次提交是HEAD^,上上次是HEAD^^,也可以写成HEAD～2 ,依次类推。
git push origin master -f
```



## 分支

- 自建的github仓库存在两个分支：main和master，之前代码push到master分支，需将master分支上的代码合并到main分支。2021年8月后，github默认分支为main

```bash
git checkout main
# 切换到分支 'main'
# 您的分支与上游分支 'origin/main' 一致
git branch
# * main
#  master
git merge master --allow-unrelated-histories
# 将master分支合并到main上
# Merge made by the 'recursive' strategy
git pull origin main
git push origin main
```



## 扩展

### alias别名，优化提交

- 因为平时提交总是↓，又长又臭

```bash
git commit -m "名字"
```

- 所以可以用别名‘c’ 代替‘commit -m’

```bash
git config --global alias.cm="commit -m"
```

- 下次提交直接就可以

```bash
git c "第n次提交"
```

### 文件处理命令

ls：查看文件夹有什么文件
cd：进入文件
clip：复制文件
