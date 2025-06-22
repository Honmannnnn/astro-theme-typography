---
title: Vue基础入门
pubDate: 2022-09-01
categories: ['Vue']
description: 'Vue.js：构建现代、高效、灵活的前端应用'
slug: Introduction to Vue Basics
---

# Vue.js基础入门

## 1.什么是Vue

​	Vue读音类似View，是一套用于构建用户界面的渐进式框架与其他大型框架（Angular、React...）相比,Vue被设计为可以自底向上逐层应用。而其他大型框架需要一开始就对项目的技术方案进行强制性的要求，Vue则更灵活，我们既可以选择Vue来开发一个全新项目，也可以将Vue引入到一个现有的项目中。

​	Vue的数据驱动是通过MVVM（Model-View-ViewModel）的模式来实现的，基本工作原理如下图所示：

![image-20220901214716518](/images/Vue/1.png)

## 2.Vue的优势

> 前端主流的框架有Angular、React、**Vue**。

1. 轻量级
2. 数据绑定（数据双向绑定。）
3. 指令 （v-for列表渲染、v-if条件渲染、v-bind动态绑定指令。）
4. 插件 （对框架的功能进行扩展，通过MyPlugin.install完成插件的编写，简单配置后就可以全局使用。）

## 3.Vue开发环境

1. VS Code编辑器
2. git-bash命令工具
3. Node.js环境
4. npm包管理工具 （npm的服务器在国外，使用npm下载软件包的速度犹如龟速，所以解决办法要么换国内镜像，要么用vpn。）
5. Chrome浏览器和vue-devtools扩展

## 4.webpack 打包工具

### 1.安装webpack

命令行执行下面命令：

```bash
npm install webpack@4.27.x webpack-cli@3.x -g
```

**这里其实我也不知道为什么课本一定要这个版本？？？**

**webpack-cli是脚手架工具 “-g”表示全局安装。**

> > 我安装的时候就遇到了权限问题，只需要在终端输入如下命令就可以了。

```bash
sudo s
```

### 2.webpack简单使用

1.创建一个vue\chapter\demo01\demo02目录。

2.在demo02目录中创建example.js文件，文件内编辑如下代码：

```js
function add(a,b){
    return a + b
}
console.log(add(1,2)) //a=1,b=2
```

**上面的代码是计算显示a b两个数字之和，会在控制台中输出计算的结果。**

3.用终端在demo02目录下执行下面的命令（打包操作）：

```cmd
webpack example.js -o app.js
```

**上面的命令执行后会编译example.js文件，将编译好的结果保存为app.js文件。**

> > 但是我非常不幸运，我的node.js版本是17.9.0，回车之后抛出了异常（error:03000086:digital envelope routines::initialization error）。
> >
> > 原因：node.js V17版本中最近发布的OpenSSL3.0，而OpenSSL3.0对允许算法和密钥大小增加了严格的限制，可能会对生态系统造成一些影响。
> >
> > 在node.js V17以前一些可以正常运行的的应用程序，在 V17 版本就可能会抛出异常。
> >
> > 我的解决办法：
> >
> > 使用npm安装n (node版本管理n)来达到降级的目的。命令如下：
> >
> > ```bash
> > npm install -g n #安装n
> > ```
> >
> > ```bash
> > n stable #安装稳定版本
> > ```
> >
> > **拓展：**
> >
> > ```bash
> > # 升级到稳定版
> > sudo n stable
> > # 升级到最新版
> > sudo n lastest
> > # 查看所有node版本
> > sudo n ls
> > # 切换使用node版本
> > sudo n 12.13.0
> > # 切换node 版本（输入上下键盘选择确认）：
> > sudo n
> > # 删除某个node版本
> > sudo n rm 12.13.0
> > # 用指定版本执行脚本
> > sudo n use 12.13.0  xxx.js
> > ```
> >
> > 

4.创建example.html文件，引入app.js文件。html代码如下：

```html
<script src="app.js"></script>
```

5.在浏览器中打开example.html，按F12查看控制台即可看到a+b的结果(3)。



