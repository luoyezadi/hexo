title: sonar环境部署
author: LZH
categories: ["sonar"]
date: 2023年1月30日09:32:36
tags:

  - sonar
  - idea

---

### 


## sonar环境安装

安装数据库,开源的可以用 mysql 或者 postgresql 。官网上已经声明 sonarQube 7.9 版本以上不再支持 mysql 了，我们为了以后升级新版本不做数据库迁移，尽量使用 **postgresql** 。

### 1.初始化

```shell
mkdir -p /data/sonar/postgres/postgresql
mkdir -p /data/sonar/postgres/data

mkdir -p /data/sonar/sonarqube
chmod 777 -R /data/sonar/sonarqube
echo "vm.max_map_count=262144" > /etc/sysctl.conf
sysctl -p
```

### 2.dockercompose配置文件

vim /data/sonar/sonar-compose.yml

```yml
version: '3'
services:
  postgres:
    image: postgres:latest
    container_name: postgres
    restart: always
    privileged: true
    networks:
      - sonar
    volumes:
      - /data/sonar/postgres/postgresql:/var/lib/postgresql
      - /data/sonar/postgres/data:/var/lib/postgresql/data
      - /etc/localtime:/etc/localtime:ro
    ports:
      - "5432:5432"
    environment:
      POSTGRES_USER: sonar 
      POSTGRES_PASSWORD: sonar 
      POSTGRES_DB: sonar 
      TZ: Asia/Shanghai 

  sonar:
    image: sonarqube:8.9.10-community
    container_name: sonar
    restart: always
    privileged: true
    networks:
      - sonar
    volumes:
      - /data/sonar/sonarqube/logs:/opt/sonarqube/logs
      - /data/sonar/sonarqube/conf:/opt/sonarqube/conf
      - /data/sonar/sonarqube/data:/opt/sonarqube/data
      - /data/sonar/sonarqube/extensions:/opt/sonarqube/extensions
    ports:
      - "9090:9000"
    links:
      - "postgres:postgres"  
    environment:
      ALLOW_EMPTY_PASSWORD: "yes"
      SONARQUBE_JDBC_USERNAME: sonar
      SONARQUBE_JDBC_PASSWORD: sonar
      SONARQUBE_JDBC_URL: "jdbc:postgresql://postgres:5432/sonar" 

networks:
  sonar:
    driver: bridge

```

### 3.运行容器

```shell
cd /data/sonar
docker-compose -f sonar-compose.yml up -d
```



### 4.安装中文插件(离线安装)

```shell
cd sonarqube/extensions/downloads/
wget https://github.com/xuhuisheng/sonar-l10n-zh/releases/download/sonar-l10n-zh-plugin-1.24/sonar-l10n-zh-plugin-1.24.jar
docker restart sonar
```

### 5.修改权限

出现错误：ERROR: Not authorized. Analyzing this project requires to be authenticated. Please provide the values of the properties sonar.login and sonar.password.

修改权限

#### 进入sonarqube管理界面，点击【配置】、【权限】、将【Force user authentication】关闭。



## maven-sonar 插件

maven-sonar 插件，本质是一个 sonar-runner 扫描工具，也是一个客户端。根据 官方 maven-sonar 插件配置教程[SonarScanner for Maven | SonarQube Docs](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner-for-maven/) 完成 Maven setting.xml 配置。

### 1.添加 maven-sonar 插件

在 maven的setting.xml文件中pluginGroups 节点下，添加一个子节点：

```xml
<pluginGroup>org.sonarsource.scanner.maven</pluginGroup>
```

### 2.添加 sonar 的 profile

在 profiles 节点下添加一个子节点，配置 sonar 插件的主机 URL：

```xml
    <profile>
        <id>sonar</id>
        <activation>
            <activeByDefault>true</activeByDefault>
        </activation>
        <properties>
            <sonar.host.url>
              http://192.168.11.253:9090
            </sonar.host.url>
        </properties>
    </profile>
```

### 3.maven扫描命令

```shell
mvn compile sonar:sonar
```






