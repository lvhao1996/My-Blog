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
  ![DASP官网](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/DASP%E5%AE%98%E7%BD%91.png?raw=true)
  &nbsp;
  点击 “DASP Modules” 下载安装包，官网提供了 1.4~3.0 的各版本，注册后即可下载对应版本的安装包 (如果无法下载，可通过此链接：_<https://pan.baidu.com/s/1xS_xmUxUl-49hBG8eWnZDA>_
  提取码:dasp 获取3.0版本的DASP)
  &nbsp;
  ![DASP安装包](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/DASP%E5%AE%89%E8%A3%85%E5%8C%85.png?raw=true)
  &nbsp;
  在电脑 C盘 中创建名为 “dasp” 的文件夹，将下载好的压缩包解压到该文件夹中
  &nbsp;
  ![安装包存储路径](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/%E5%AE%89%E8%A3%85%E5%8C%85%E5%AD%98%E5%82%A8%E8%B7%AF%E5%BE%84.png?raw=true)
  进入“modules”文件夹，复制该文件夹的存储路径
  &nbsp;
  ![安装模块路径](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/%E5%AE%89%E8%A3%85%E6%A8%A1%E5%9D%97%E8%B7%AF%E5%BE%84.png?raw=true)
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
  ![安装成功界面](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/%E5%AE%89%E8%A3%85%E6%88%90%E5%8A%9F%E7%95%8C%E9%9D%A2.png?raw=true)
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
  ![安装成功界面](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/%E5%AE%89%E8%A3%85%E6%88%90%E5%8A%9F%E7%95%8C%E9%9D%A2.png?raw=true)
  &nbsp;
  **注：如果安装后没有出现上述界面，则可能是一些人自定义了stata命令的安装路径，这时便需要在stata的安装目录下新建一个profile.do文件，并在里面输入 _daspmenu，之后再保存即可，如果之前已经设置了profile.do文件，则只需要在文件中添加 _daspmenu，然后保存即可**
  &nbsp;
  ![stata安装目录](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/stata%E5%AE%89%E8%A3%85%E7%9B%AE%E5%BD%95.png?raw=true)
  &nbsp;
  ![profile.do文件](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/profiledo%E6%96%87%E4%BB%B6.png?raw=true)


#### 3. DASP使用
详细的DASP使用教程可参考DASP官方发布的用户手册(上文分享的安装包中包含用户手册，可自行取用，也可以直接在官网下载用户手册)
&nbsp;
  ![DASP用户手册界面](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/DASP%E7%94%A8%E6%88%B7%E6%89%8B%E5%86%8C%E7%95%8C%E9%9D%A2.jpg?raw=true)
&nbsp;
这里以绘制洛伦兹曲线和计算基尼系数为例，简要介绍DASP模块的使用

- **洛伦兹曲线**
  &nbsp;
  导入stata自带的1988年美国妇女工资数据 nlsw88.dta
  &nbsp;
  依此选择菜单栏中的“用户” → “DASP” → “Inequality” → “Lorenz/concentration curves
    ![洛伦兹曲线菜单栏](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/%E6%B4%9B%E4%BC%A6%E5%85%B9%E6%9B%B2%E7%BA%BF%E8%8F%9C%E5%8D%95%E6%A0%8F.png?raw=true)
  &nbsp;
  之后会出现如下对话框，在对应的复选框中选择自己想要计算的变量，就可以绘制出该变量的洛伦兹曲线 (图中其他的复选框可根据自己的计算需要选取相应的变量，具体含义可参考DASP用户手册，里面有详细的说明)
  &nbsp;
    ![洛伦兹曲线对话框](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/%E6%B4%9B%E4%BC%A6%E5%85%B9%E6%9B%B2%E7%BA%BF%E5%AF%B9%E8%AF%9D%E6%A1%86.png?raw=true)
  &nbsp;
  此处选取了88年妇女工资wage变量作为Welfare variable(s) ，洛伦兹曲线如下图所示
  &nbsp;
    ![88年美国妇女工资洛伦兹曲线](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/88%E5%B9%B4%E7%BE%8E%E5%9B%BD%E5%A6%87%E5%A5%B3%E5%B7%A5%E8%B5%84%E6%B4%9B%E4%BC%A6%E5%85%B9%E6%9B%B2%E7%BA%BF.png?raw=true)
  &nbsp;

- **基尼系数**
  &nbsp;
  基尼系数的计算和洛伦兹曲线的绘制步骤基本一致，只是需要在弹出的“Inequality” 菜单中选择 “Inequality/concentration indices” 
  &nbsp;
    ![基尼系数菜单栏](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/%E5%9F%BA%E5%B0%BC%E7%B3%BB%E6%95%B0%E8%8F%9C%E5%8D%95%E6%A0%8F.png?raw=true)
  &nbsp;
  和绘制洛伦兹曲线一样，此处选取了88年妇女工资wage变量作为Welfare variable(s) ，基尼系数计算结果如下图所示
  &nbsp;
    ![88年美国妇女工资基尼系数](https://github.com/lvhao1996/picBed/blob/master/Stata/DASP-Introduce/88%E5%B9%B4%E7%BE%8E%E5%9B%BD%E5%A6%87%E5%A5%B3%E5%B7%A5%E8%B5%84%E5%9F%BA%E5%B0%BC%E7%B3%BB%E6%95%B0.png?raw=true)
  &nbsp;

#### 4. 一些补充
&nbsp;
除了DASP模块之外，stata中还有许多可以用来计算不平等指数的外部命令，比如 **ineqdeco**、**lorenz** 等，大家可以通过查看stata的帮助文件进行使用

  


