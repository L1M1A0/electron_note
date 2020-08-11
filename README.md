# electron-note

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).




### ----------------------- 笔记 -----------------------
### 配置工程 
注：用于node_modules文件太大了，所以在上传到github等的时候将其删除，但需要重新配置

1. cd 项目目录
2. npm install。 注：配置node_modules依赖，会自动把原工程中已经配置好的依赖都安装完成。
3. npm run electron:serve。注：运行查看安装之后是否能正确显示


### 环境安装
Mac下vue-cli的全局安装和卸载
查看版本：vue -V

卸载：
1. 首先需要开放用户权限：sudo chmod -R 777 /usr/local/lib/node_modules/
2. 卸载2.0版本：npm uninstall vue-cli -g
3. 查看版本：vue -V 
4. 安装新版本：npm install -g @vue/cli
 
tips：失败可以尝试使用管理员身份安装和卸载



### 参考文章
Electron 入门 - Electron的进程介绍及创建项目的三种方式
https://www.jianshu.com/p/153ca73b7e46

electron教程系列 
https://www.cnblogs.com/silenzio/p/11580104.html


### 从零开始创建 electron 工程

方法1. 使用vue-cli创建electron项目（在预览程序Launching Electron的时候耗时比较长，文件比较大）

1.1 步骤如下：

1.1.1 安装npm,vue-cli，如果安装失败，可能需要开启权限

1.1.2 使用vue-cli创建项目：vue create 项目名称

1.1.3 Vue项目中引入electron发布桌面应用：vue add electron-builder（注：https://www.cnblogs.com/ezhar/p/13163595.html）

1.2 思路：

1.2.1 用vue-cli创建项目，同时可以用vue命令语句来安装其他依赖

1.2.2 配置electron的开发环境

1.3 创建流程示例

1.3.1 cd /Users/LZBiao/Desktop/未命名文件夹

1.3.2 vue create zbmusic（注：创建项目，然后开始设置基础配置信息）

1.3.3 vue add electron-builder（注：在项目创建完成后，引入项目，并增加electron开发环境）

1.3.4 npm run electron:serve（注：在上一步之后可以使用这句命令来验证环境是否安装成功，成功会打开一个新窗口）



方法2：使用官方提供的项目来修改


方法3：(按照教程操作)

https://www.cnblogs.com/donghuang/p/12297148.html



### 增加其他框架 
1. element-ui：vue add element。前端ui框架

2. umy-ui：npm install umy-ui。用来解决element-ui加载大量列表的时候，卡顿的问题。替代作用










