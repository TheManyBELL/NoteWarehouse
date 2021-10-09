# 【vuforia】基本使用流程 以Cylinder为例

## 前置工作

### 1.注册vuforia官方账号并登录

[vuforia官方网站](https://developer.vuforia.com/)

### 2.获取产品密钥

产品密钥将作为ARcamera对象的配置属性，至少在后续打安卓安装包时要验证

在官网点击Develop标签，选择License Manger，选择Get Development Key

在这个页面创建好项目名称，确认即可获得密钥

### 3.下载vuforia引擎

在官网的Download页面下载unity版本的引擎，用最新版就行

### 4.启动unity，导入vuforia引擎

创建一个普通的3D空项目即可，

>  Assests→import Package→在文件管理页面找到vuforia引擎

## 正式开始

### 1.配置相机

删除unity3d主动给你加的MainCamera

加入AR专用的相机ARcamera

> GameObejct→Vuforia Engine→ARcamera

在ARcamera的inspector页面的下方，点击`open Vuforia Engine congfiguration`

在跳转到的新的页面的`App License Key`中输入前置工作中得到的产品密钥

然后也不用确认

### 2.加入CylinderTarget

这是vuforia专用的圆柱体对象

加完后并没有什么效果，接下来要去挂网建立圆柱体AR模型

### 3.构建圆柱体AR模型

- 为什么要构建AR模型？

  AR的工作原理是将虚拟模型和现实物体进行映射，简单来说，就是要为现实中存在的物体建立一模一样的模型（主要指外观、大小）。

在官网进入Target Manager页面

> Develop→Target Manager

然后构建数据库

> Add Database→输入数据库名称→选择Type为Device

点击建立好的数据库，开始构建AR对象

> add target→选择Type，这里是Cylinder→输入模型维度，单位是米，要输入现实中物体的真实大小→命名→Add

可以看到建好的AR对象的状态还是`incomplete`，这表示模型不可用

接下来就是让模型可用，点击模型，进入编辑页面

编辑页面中vuforia很贴心的展示了物体的三维模型，你可以转动它，右边是等待你上传的贴图，

> 明明你建的是标准圆柱体，但网页展示给你的三维模型是个平截锥体，不用在意

上传贴图要求长宽像素比符合模型实际大小，自己算算就行

贴图贴完就可以用了！

返回数据库网页，选中我们已经是`Active`状态的模型，点击download Database打包模型并下载

### 4.将AR模型导入unity

>  Assests→import Package→在文件管理页面找到刚下载的数据库包（模型包）

### 5.配置Cylinder Target对象

Cylinder Target终于不会一无所有了，点击Cylinder Target，在inspector页面选择Database和Cylinder Target，这时候屏幕中就出现了我们建好的圆柱体模型

