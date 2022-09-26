title: HEXO初始化
author: LZH
categories: ["初始化"]
date: 2022-9-26 17:05:17
tags:

  - 初始化

---



## 1.清除缓存



```shell
npm install && rm -rf ./public
```

## 2.安装hexo-cli

``` shell
npm install hexo-cli -g
```

## 3.安装git插件

```shell
npm install
npm install hexo-deployer-git --save
```

## 4.解决hexo搜索问题

```shell
npm i hexo-generator-json-content --save
```

## 5. 解决本地图片问题

### 5.1 修改配置文件(用typory时不用修改)

​		修改文件_config.yml 里的post_asset_folder:这个选项设置为true
这个时候创建新的文章时会在_posts文件下自动生成一个与新建文件同名的文件夹。

### 5.2安装插件

```shell
npm install https://github.com/CodeFalling/hexo-asset-image -- save
```

**注意 不要使用`npm install hexo-asset-image --save`这个命令安装,版本号不对**

**在md中书写格式（相对路径）**

在md使用如下形式引用图片

> ```shell
> ![01](md文件名/01.jpg)
> ```



## 6.完整giteego脚本

```yaml
version: '1.0'
name: master-pipeline
displayName: MasterPipeline
triggers:
  trigger: auto
  push:
    branches:
      include:
        - master
variables:
  global:
    - REPO
stages:
  - name: compile
    displayName: 编译
    strategy: naturally
    trigger: auto
    steps:
      - step: build@nodejs
        name: build_nodejs
        displayName: Nodejs 构建
        nodeVersion: 14.16.0
        commands:
          - npm install && rm -rf ./public
          - ''
          - npm install hexo-cli -g
          - ''
          - hexo version
          - npm install
          - npm install hexo-deployer-git --save
          - npm i hexo-generator-json-content --save
          - npm install https://github.com/CodeFalling/hexo-asset-image -- save
          - git config --global user.email "451447840@qq.com"
          - git config --global user.name "luoyezadi"
          - npm run config deploy.repo $REPO
          - rm -rf .deploy_git
          - git config --global core.autocrlf false
          - echo "hexo deploy"
          - hexo clean && hexo g && hexo d
          - ''
          - ''
        strategy: {}

```

其中REPO为全局变量配置(https://luoyezadi:xxxx@gitee.com/luoyezadi/blog.git)即可，xxxx为密码

```yaml
variables:
  global:
    - REPO
```



## 7.实例

![image-20220926171830024](HEXO初始化/image-20220926171830024-16641839142027.png)
