# 入门

git是一种源码管理系统（source code management）它对当前文件提供版本管理功能，核心思想是对当前文件建立一个对象数据库，将历史版本信息存放在这个数据库中

## Git 安装

第一步：根据平台选择下载安装[Git](https://gitforwindows.org/)

```powershell
# 测试是否安装成功，显示版本号，则表示安装成功。
git --version
```

第二步：初始化Git配置

```powershell
# 显示当前的Git配置
$ git config --list
# 设置提交代码时的用户信息
$ git config --global user.name "[name]"
$ git config --global user.email "[email address]"
```

第三步：上传公钥

```powershell
# 生成私钥和公钥
ssh-keygen -t rsa -C "your@email.com"
# 查看公钥
Linux： cat ~/.ssh/id_rsa.pub
windows：C:\Users\用户\.ssh
```

<img src='https://i.loli.net/2020/07/31/H5CQ4FzhwjplO3R.png'>

第四步：在Github上[创建项目](https://github.com/new)

<img src='https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/1/9/16832a21624a4f6d~tplv-t2oaga2asx-zoom-in-crop-mark:1304:0:0:0.awebp'>

第五步：初始化代码并上传

```powershell
echo "# a" >> README.md 
git init 

## 添加文件
git add README.md

# 添加git提交信息
git commit -m "first commit"

## 项目关联远程仓库(ssh或者SSL)或者先clone代码 注意添加自己的Git地址
git remote add origin https://XXXX.git

## 项目推送到master分支
git push -u origin "master"
```
