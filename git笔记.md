## git命令行

ls：查看文件夹有什么文件
cd：进入文件
clip：复制文件

```css
clip < -/c/Users/锋锋的沉默/.ssh/id_rsa.pub
```


git init：交给git管理

### 设置名字和邮箱，相当于注册账号密码
```css
git config --global user.name "wyf"
git config --global user.email "wangyifeng668@qq.com"
```

### 生成密钥

```css
ssh-keygen -t -rsa -C"wangyifeng668@qq.com"

```

```css
如果出现"unkown key type -rsa"就输入ssh-keygen -t -rsa就好了
```

### 回到GitHub

```css
settings -> SSH and GpG keys -> 填写title和key值(~/ssh/id_rsa.pub)
```

### 连接远程仓库

```css
git remote add origin + ssh地址
```

### 首次提交必须进行过一次提交

```css
git push --set-upstream origin master
```

##### 本地区  -> 暂存区

```css
git add 文件名 /*提交单个文件*/
git add . /*提交全部内容*/
```

##### 暂存区 -> 历史记录区

```css
git commit -m "王译锋的第一次提交"
```

##### 历史记录区 -> 提交到gitHub上

```css
git push
```

### 查看当前仓库的状态，看看内容有没有被修改过

```css
git status
```

### 查看每次的改变

```css
git diff
```

### 删除文件

```css
rm 文件名
```

### 后悔药

```css
git checkout -- .
```

### 查看commit的记录

```css
git log/*输入字母Q自动退出*/
```

```css
git reflog（简洁版，查看版本号）
```

### 回到以前的版本

```css
git reset --hard 版本号
```

### 从git上拉代码

```css
git clone 仓库的ssh
```

### 删除之前的提交

```css
git reset --hard HEAD^/*HEAD是指向最新的提交，上一次提交是HEAD^,上上次是HEAD^^,也可以写成HEAD～2 ,依次类推。*/
git push origin master -f
```

