---
title: Quick Start for Nacos
keywords: [Nacos,Quick start]
description: This topic is about how to set up and use Nacos.
---

# Quick Start for Nacos

This topic is about how to set up and use Nacos.

## 0.Choose Version

Nacos 1.X is old version. Recommend you use 2.X version. Please move to [document](./v2/quickstart/quick-start.md).

You can see the introduction of each version at [release notes](https://github.com/alibaba/nacos/releases) or [blog](https://nacos.io/zh-cn/blog/index.html), the current recommended version is 2.2.3.

## 1.Prerequisites

Before you begin, install the following:

1. 64bit OS: Linux/Unix/Mac/Windows supported, Linux/Unix/Mac recommended.
2. 64bit JDK 1.8+: [downloads](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html), [JAVA_HOME settings](https://docs.oracle.com/cd/E19182-01/820-7851/inst_cli_jdk_javahome_t/).
3. Maven 3.2.x+: [downloads](https://maven.apache.org/download.cgi), [settings](https://maven.apache.org/settings.html).

## 2.Download & Build from Release

There are two ways to get Nacos. 

### 1)Download source code from Github
  
```bash
git clone https://github.com/alibaba/nacos.git
cd nacos/
mvn -Prelease-nacos -Dmaven.test.skip=true clean install -U 
ls -al distribution/target/

// change the $version to your actual path
cd distribution/target/nacos-server-$version/nacos/bin
```
  
### 2)Download run package 

Select the latest stable version from https://github.com/alibaba/nacos/releases

```bash
  unzip nacos-server-$version.zip  OR tar -xvf nacos-server-$version.tar.gz
  cd nacos/bin
```  

## 3.Start Server

### Linux/Unix/Mac

Run the following command to start(standalone means non-cluster mode):
 
`sh startup.sh -m standalone`

If you are using a ubuntu system, or encounter this error message [[symbol not found, try running as follows:

`bash startup.sh -m standalone`

### Windows

Run the following command to start(standalone means non-cluster mode):

`cmd startup.cmd -m standalone`

## 4.Service & Configuration Management

### Service registration

`curl -X POST 'http://127.0.0.1:8848/nacos/v1/ns/instance?serviceName=nacos.naming.serviceName&ip=20.18.7.10&port=8080'`

### Service discovery

`curl -X GET 'http://127.0.0.1:8848/nacos/v1/ns/instance/list?serviceName=nacos.naming.serviceName'`

### Publish config

`curl -X POST "http://127.0.0.1:8848/nacos/v1/cs/configs?dataId=nacos.cfg.dataId&group=test&content=helloWorld"`

### Get config

`curl -X GET "http://127.0.0.1:8848/nacos/v1/cs/configs?dataId=nacos.cfg.dataId&group=test"    `

## 5.Shutdown Servers

### Linux/Unix/Mac

`sh shutdown.sh`

### Windows

`cmd shutdown.cmd`

Or click the `shutdown.cmd` file operation.
