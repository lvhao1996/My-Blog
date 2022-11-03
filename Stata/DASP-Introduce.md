## Stata 模块 DASP 安装及使用教程 (可计算基尼系数)
[TOC] 
<!-- 自动生成目录 -->
#### 1. DASP简介
DASP全称为 _"Distributive Analysis Stata Package"_ ，它是一个综合性的 stata 模块包，可以用来分析某个变量取值的分布情况，特别是一些经济变量在不同个体之间的分配情况。除了人们熟悉的基尼系数外，它还可以计算阿特金森指数、广义熵指数等表示不平等的指标。

DASP模块由加拿大拉瓦尔大学 (Université Laval) 的 Abdelkrim Araar 和 Jean-Yves Duclos 开发，现在已经更新到 3.03 版，用它来计算基尼系数等不平等指标十分方便，该模块的开发由加拿大政府和世界银行、联合国开发计划署等国际机构资助，可以**免费获取**。

#### 2. DASP安装

DASP官网 _(<http://dasp.ecn.ulaval.ca/>)_ 提供了两种安装方式,一种是本地安装，即在官网下载安装包后进行安装，另一种是在线安装，不用下载安装包。相比来说，后者更方便一些，建议采用在线安装的方式进行安装。

- **本地安装** (以安装DASP3.03为例)
  &nbsp;
  **注：DASP3.0要求stata15.0或更高版本**
  &nbsp;
  进入DASP官网 _(<http://dasp.ecn.ulaval.ca/>)_
  ![官网截图](DASP/web.png)
  &nbsp;
  点击 “DASP Modules” 下载安装包，官网提供了 1.4~3.0 的各版本，注册后即可下载对应版本的安装包 (如果无法下载，可通过此链接：_<https://pan.baidu.com/s/1xS_xmUxUl-49hBG8eWnZDA>_
  提取码:dasp 获取3.0版本的DASP)
  &nbsp;
  ![官网截图](DASP/modules.png)
  &nbsp;
  在电脑 C盘 中创建名为 “dasp” 的文件夹，将下载好的压缩包解压到该文件夹中
  &nbsp;
  ![文件路径截图](DASP/package.png)
  进入“modules”文件夹，复制该文件夹的存储路径
  &nbsp;
  ![文件路径截图](DASP/install.png)
  &nbsp;
  打开stata, 在命令窗口输入以下命令
  &nbsp;
  ```stata
     net from C:\dasp\DASP_V3.03\modules 
     net install dasp_p1, force 
     net install dasp_p2, force 
     net install dasp_p3, force 
     net install dasp_p4, force 
     net install dasp_p5, force 
     net install dasp_p6, force 
     cap adddmenu profile.do _daspmenu 
     cap add_data_examples
  ```
  &nbsp;
  若出现以下界面则表示安装成功
  &nbsp;
  ![stata界面截图](DASP/stata.png)
  &nbsp;

- **在线安装**(以安装DASP3.03为例)
  &nbsp;
  在线安装比较简单，直接在stata命令窗口输入以下代码即可
  &nbsp;
  ```stata
  net from http://dasp.ecn.ulaval.ca/dasp3 
  net install dasp_p1, force 
  net install dasp_p2, force 
  net install dasp_p3, force 
  net install dasp_p4, force 
  net install dasp_p5, force 
  net install dasp_p6, force 
  cap adddmenu profile.do _daspmenu 
  cap add_data_examples 
  ```
  同本地安装一样，若出现以下界面则表示安装成功
  &nbsp;
  ![stata界面截图](DASP/stata.png)
  &nbsp;
  **注：如果安装后没有出现上述界面，则可能是一些人自定义了stata命令的安装路径，这时便需要在stata的安装目录下新建一个profile.do文件，并在里面输入 _daspmenu，之后再保存即可，如果之前已经设置了profile.do文件，则只需要在文件中添加 _daspmenu，然后保存即可**
  &nbsp;
  ![文件路径截图](DASP/profiledo.png)
  &nbsp;
  ![文件路径截图](DASP/profiledo2.png)


#### 3. DASP使用
详细的DASP使用教程可参考DASP官方发布的用户手册(上文分享的安装包中包含用户手册，可自行取用，也可以直接在官网下载用户手册)
&nbsp;
  ![官网界面截图](DASP/manuals.jpg)
&nbsp;
这里以绘制洛伦兹曲线和计算基尼系数为例，简要介绍DASP模块的使用

- **洛伦兹曲线**
  &nbsp;
  导入stata自带的1988年美国妇女工资数据 nlsw88.dta
  &nbsp;
  依此选择菜单栏中的“用户” → “DASP” → “Inequality” → “Lorenz/concentration curves
  &nbsp;
  之后会出现如下对话框，在对应的复选框中选择自己想要计算的变量，就可以绘制出该变量的洛伦兹曲线 (图中其他的复选框可根据自己的计算需要选取相应的变量，具体含义可参考DASP用户手册，里面有详细的说明)
  &nbsp;
    ![洛伦兹菜单截图](DASP/lorenz2.png)
  &nbsp;
  此处选取了88年妇女工资wage变量作为Welfare variable(s) ，洛伦兹曲线如下图所示
  &nbsp;
    ![洛伦兹菜单截图](DASP/lorenz3.png)
  &nbsp;

- **基尼系数**
  &nbsp;
  基尼系数的计算和洛伦兹曲线的绘制步骤基本一致，只是需要在弹出的“Inequality” 菜单中选择 “Inequality/concentration indices” 
  &nbsp;
    ![基尼系数截图](DASP/gini.png)
  &nbsp;
  和绘制洛伦兹曲线一样，此处选取了88年妇女工资wage变量作为Welfare variable(s) ，基尼系数计算结果如下图所示
  &nbsp;
    ![基尼系数截图](DASP/gini2.png)
  &nbsp;

#### 4. 一些补充
&nbsp;
除了DASP模块之外，stata中还有许多可以用来计算不平等指数的外部命令，比如 **ineqdeco**、**lorenz** 等，大家可以通过查看stata的帮助文件进行使用

  


