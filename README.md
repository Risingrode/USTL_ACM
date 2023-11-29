# 前言

## 初衷

为了让大家学习算法，为以后的ACM打好基础。

# 环境安装

## python



3.8以上版本即可，pip需要正常使用



## Typora

用于编写md文档

[百度云](https://pan.baidu.com/s/1tYXxScsFEtxfErnhnhJXqQ?pwd=2w23 
提取码：2w23)



## Picgo



是一个上传本地图片的软件。

图床使用[sm.ms](https://sm.ms/)，记得去CSDN上面搜索配置教程哦。




# 如何使用



##  fork我的项目

![](https://s2.loli.net/2023/11/24/vmAwM26FGKpztVg.png)

这时这个项目会出现在你的仓库里面。🤣

复制`你的仓库里面的链接`，你的git链接差不多就是`https://github.com/<你的github名字>/USTL_ACM.git`。

![](https://cwrisingblog.oss-cn-beijing.aliyuncs.com/blog/20231129224756.png)



## git到你的本地

在桌面随便创建一个文件夹，打开git终端`git bash here`，输入下面命令。

`git clone https://github.com/Risingrode/USTL_ACM.git`

你会看到下面界面，成功了！！！😂

![](https://cwrisingblog.oss-cn-beijing.aliyuncs.com/blog/20231129225026.png)



## 安装 mkdocs

`接下来需要python，随便在命令行黑框里面运行即可`

```
下载链接：pip install mkdocs
```

## 安装网站主题

本站主题是material，使用下面命令进行安装即可。

```
pip install mkdocs-material
```

## 安装其它依赖

```
pip install pymdown-extensions
pip install mkdocs-awesome-pages-plugin
```

## 安装i18n

这里是个坑，我安装的时候，直接安装`pip install i18n`不行，你需要专门安装mkdocs下的i18n,然后问的chatGPT,他给我提供的解决方案是`pip install mkdocs-i18n-plugin`;可惜不对，最后在谷歌上找到下面命令，就对了。

```
pip install mkdocs-static-i18n
```

## 运行项目

```
mkdocs serve
```

## 构建静态网站文件

```
mkdocs build
```

## 一键推送

```
mkdocs gh-deploy
```

会在GitHub项目上创建一个gh-pages分支，并执行mkdocs build命令，然后将当前目录中的site目录下的内容推送到远程的gh-pages分支。

每当你写完代码后想要提交的话，直接点击`buildAndPush.bat`文件即可，一键提交，其他的就不用管了。




## 如何把自己写的文章加入网站中

写文档的文件在docs目录下面

![](https://cwrisingblog.oss-cn-beijing.aliyuncs.com/blog/20231129225913.png)

在docs里面写好文档之后，需要修改`mkdocs.yml`文件，把你写的文档配置到网站中。

![](https://cwrisingblog.oss-cn-beijing.aliyuncs.com/ustl_acm/20231129230207.png )

这里是导航栏配置，自己看看就明白了

![](https://cwrisingblog.oss-cn-beijing.aliyuncs.com/ustl_acm/20231129230110.png)







## 建设日志

> 2023-09-26,构建该项目
>
> 2023-11-29, 完成说明文档







## TODO

- [x] 部署到自己的服务器上面
- [ ] 语法基础部分完成
- [ ] 算法基础部分完成
- [ ] 基础题目完成
- [ ] 算法进阶部分完成
- [ ] 进阶题目完成
- [ ] 拓展acm优质题目模块
- [ ] 增加优秀网站模块



## 贡献

该项目创建于2023-09-26日，希望大家有什么好的算法思路啥的多多贡献。



## 联系我们

辽宁科技大学ACM校队


如果你有什么好的想法，可以联系我们，我们一起来完善这个项目。如果有什么修改意见，可以提交github上的`isssue`。



## 版权声明

未经允许，不可转载









