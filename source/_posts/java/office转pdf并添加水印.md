---
title: office转pdf并添加水印
date: 2019-06-08 21:12:39
categories: java
tags:
    - java
---

# 场景介绍

项目里有上传附件的功能，不同模块上传的方式还不同，附件的格式可以是任意的。

我们有上传视频的，然后大小还是好几个 G 的那种，这样的我们选择了阿里云的产品，叫视频点播，还可以通过客户端上传，最大可支持 10G，对我们来说足够了，并且还需要转码成 mp4，因为要支持 app 播放，阿里云也是可以做到的，这个会单独写一篇。

office 文档，先需要加水印，但只有 pdf 才可以加水印，还得把文档转成 pdf，上传完后，还要支持在线预览，所以这个就需要一整套相关的东西了。转换格式>加水印>上传>在线预览。这里就依次介绍。

# 环境要求

## openOffice

- **window版本**

  下载地址：http://www.openoffice.org/download/index.html

  安装后，右键启动图标查看安装路径，通过 cmd 进入 program 路径下：

  ![](https://uploader.shimo.im/f/YhBLhLGrMJ0VdS69.png!thumbnail?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJleHAiOjE2MTg3MTg5MzIsImciOiJyS1dId2RwZ1FqZEhXOHFRIiwiaWF0IjoxNjE4NzE3MTMyLCJ1IjoxNzM0MjgzMH0.Zyu1ZTjegAfxWtEaU1xgGqwUT8vzQ7piiStlifa_2IU)

  启动服务命令：`soffice -headless -accept="socket,host=127.0.0.1,port=8100;urp;"`

- **linux版本**

  下载地址：https://pan.baidu.com/s/19ZUzTGZ2_QKVlfZEWpBicQ

  注：这个其实是一个文件预览的插件，并且这个预览也是在我们项目里有用到的，所以就一并安装了，在 linux 上解压启动，他会自动安装 openOffice，安装路径为：/opt/openoffice4，解决了 openOffice 安装的繁琐步骤。

  ![](https://uploader.shimo.im/f/4SlIjHYItn4hd3KQ.png!thumbnail?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJleHAiOjE2MTg3MTg5MzIsImciOiJyS1dId2RwZ1FqZEhXOHFRIiwiaWF0IjoxNjE4NzE3MTMyLCJ1IjoxNzM0MjgzMH0.Zyu1ZTjegAfxWtEaU1xgGqwUT8vzQ7piiStlifa_2IU)

  启动服务命令：`/opt/openoffice4/program/soffice -headless -accept="socket,host=127.0.0.1,port=8100;urp;" -nofirststartwizard &`

  ![](https://uploader.shimo.im/f/UtNVauKmVQUTBMp8.png!thumbnail?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJleHAiOjE2MTg3MTg5MzIsImciOiJyS1dId2RwZ1FqZEhXOHFRIiwiaWF0IjoxNjE4NzE3MTMyLCJ1IjoxNzM0MjgzMH0.Zyu1ZTjegAfxWtEaU1xgGqwUT8vzQ7piiStlifa_2IU)

  注：后来发现这种启动方式只能本地连接，远程不行将host=的ip地址写为0.0.0.0就可以通过java远程连接了

  查看端口：`netstat -lnp |grep 8100`

## JodConverter

转 pdf 需要的 jar 包工具，maven 依赖如下：

```xaml
<dependency>
    <groupId>com.artofsolving</groupId>
    <artifactId>jodconverter</artifactId>
    <version>2.2.1</version>
</dependency>
<dependency>
    <groupId>com.itextpdf</groupId>
    <artifactId>itextpdf</artifactId>
    <version>5.4.2</version>
</dependency>
<dependency>
    <groupId>org.openoffice</groupId>
    <artifactId>jurt</artifactId>
    <version>3.0.1</version>
</dependency>
<dependency>
    <groupId>org.openoffice</groupId>
    <artifactId>ridl</artifactId>
    <version>3.0.1</version>
</dependency>
<dependency>
    <groupId>org.openoffice</groupId>
    <artifactId>juh</artifactId>
    <version>3.0.1</version>
</dependency>
<dependency>
    <groupId>org.openoffice</groupId>
    <artifactId>unoil</artifactId>
    <version>3.0.1</version>
</dependency>
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-jdk14</artifactId>
    <version>1.4.3</version>
</dependency>
```

<font style='color:red'>注：</font>jodconverter 在 maven 中的版本只有 2.2.1，但有一个问题，转 pdf 的时候不兼容 pptx，docx，xlsx 这样的文档，在 2.2.2 的版本解决了这个问题，但我们想用这个兼容的版本，就要改下一 BasicDocumentFormatRegistry 类中的 getFormatByFileExtension 方法：

- 第一步：新建包：com.artofsolving.jodconverter

- 第二步：新建类：BasicDocumentFormatRegistry，代码如下：

  ```
  package com.artofsolving.jodconverter;
  import java.util.ArrayList;
  import java.util.Iterator;
  import java.util.List;
  public class BasicDocumentFormatRegistry implements DocumentFormatRegistry {
      private List documentFormats = new ArrayList();
  
      public BasicDocumentFormatRegistry() {
      }
      public void addDocumentFormat(DocumentFormat documentFormat) {
          this.documentFormats.add(documentFormat);
      }
      protected List getDocumentFormats() {
          return this.documentFormats;
      }
      @Override
      public DocumentFormat getFormatByFileExtension(String extension) {
          if (extension == null) {
              return null;
          } else {
              if (extension.indexOf("doc") >= 0) {
                  extension = "doc";
              }
              if (extension.indexOf("ppt") >= 0) {
                  extension = "ppt";
              }
              if (extension.indexOf("xls") >= 0) {
                  extension = "xls";
              }
              String lowerExtension = extension.toLowerCase();
              Iterator it = this.documentFormats.iterator();
  
              DocumentFormat format;
              do {
                  if (!it.hasNext()) {
                      return null;
                  }
                  format = (DocumentFormat)it.next();
              } while(!format.getFileExtension().equals(lowerExtension));
  
              return format;
          }
      }
      @Override
      public DocumentFormat getFormatByMimeType(String mimeType) {
          Iterator it = this.documentFormats.iterator();
  
          DocumentFormat format;
          do {
              if (!it.hasNext()) {
                  return null;
              }
              format = (DocumentFormat)it.next();
          } while(!format.getMimeType().equals(mimeType));
  
          return format;
      }
  }
  ```

  其实就是修改了带×的处理方式跟不带×的一样，这样，就可以把 pptx，docx 等这样的文档转成 pdf，然后就可以加水印了。添加类后的项目结构

  ![image-20210424164520901](C:\Users\think\AppData\Roaming\Typora\typora-user-images\image-20210424164520901.png)

# 转PDF

环境好了，开始转 pdf。代码如下：