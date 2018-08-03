# 天穹飞控
							
## 飞控简介
近10年来，小型多旋翼飞行器发展迅猛，国外涌现出无数开源项目，其中不乏一些耳熟能详的优秀开源飞控项目。而在中国，消费级多旋翼更是发展得如火如荼，其中DJI一枝独秀，占据了国内外80%的市场。然而有一点值得我们深思的是，即使到今天，国内仍然没有一个像样的开源飞控项目，只有少部分存在于淘宝上的收费开源项目，而且质量极其堪忧，其中大部分连最基本的定点悬停功能都无法实现，且代码架构混乱，缺少文档和资料，少数带有定点功能的，其效果也远远不及普通的商业飞控，更不用说和DJI之类的进行对比。更糟糕的一点是，这些收费开源飞控项目基本上都是一锤子买卖，缺少后续更新维护及性能优化，少数一些更新仅仅是小BUG修复。

在这个背景下，本飞控项目诞生了，其目的不仅仅是为了做出一款性能逼近甚至超越DJI的飞控，而是想让更多的中国人参与进飞控项目的开发，包括大学生们，各行各业的爱好者，还有各地区的行业从业者等。国外的APM/PX4飞控也是经过数百人多年的维护和优化，才有了今天的成果，但是也不得不说国外的大部分开源飞控在性能细节上的优化还没有到位，性能难以与DJI之类经过深度优化的飞控同台竞技。

而本项目的最终目标，是打造出一套易于使用和开发，且飞行性能比肩商业产品的中国本土化开源多旋翼飞控平台，为中国的多旋翼无人机产业添砖加瓦。

>飞控交流Q群：472648354

>[飞控交流论坛](http://bbs.loveuav.com/forum-68-1.html)

## 飞控特色
- 功能齐全，除了最基础的自稳、定高、定点飞行之外，还支持自动降落、自动返航、自动航线、兴趣点环绕等高级功能，在国内的开源飞控中独此一家

- 飞控使用了带硬件恒温的独立陀螺仪模块，传感器零漂更加稳定

- 飞控的姿态估计中使用了运动加速度补偿和自适应卡尔曼滤波器，极大提升了飞机在各种机动飞行状况下的姿态精度，并直接提升了惯导性能

- 导航方面使用了基于飞行状态误差模型的自适应卡尔曼滤波器，提升动态刹车精度以及悬停精度（可达到DJI的水准，后续持续优化）

- 加速度与地磁传感器的校准均使用了基于高斯牛顿法的椭球误差方程拟合算法，校准精度基本达到了廉价MEMS传感器的极限

- 使用串级PID控制算法，悬停姿态控制精度可达0.1°，且控制方面将算法实现与操控逻辑实现分开，方便代码理解及后期扩展开发

- 使用了轻量级RTOS：FreeRTOS，实现抢占式任务调度，提高系统实时性

- 使用自定义的轻量级通信协议bsklink，配合自主开发的天穹地面站软件，可实现飞控参数设置、传感器校准、波形显示分析和航线规划等功能

- 兼容mavlink协议，可使用QGroudControl及Mission Planner地面站的大部分功能如传感器校准，数据波形分析，航线规划等

- 飞控整体架构极其清晰，代码逐行注释，功能模块化且尽可能降低各模块之间的耦合程度，方便新手理解及代码移植

## 下载与编译
- 使用git克隆项目到本地

- 安装Keil MDK 5.25，编译飞控工程

>[详细图文说明](http://bbs.loveuav.com/thread-11422-1-1.html)


## 飞控硬件配置
主控：STM32F405RGT6

陀螺仪：ICM20689 （带硬件恒温）

气压计：MS5611

GPS：u-blox M8N

磁力计：视GPS模块而定

信号输入接口：PPM & SBUS

信号输出接口：4路PWM（仅支持四旋翼）

飞控正在测试中，敬请期待......

## 天穹地面站

正在开发中

![天穹地面站](https://github.com/loveuav/BlueSkyFlightControl/blob/master/PIC/BlueSkyPilot.jpg)

## QGroundControl地面站

QGroundControl是一个使用QT语言编写的跨平台开源无人机地面站项目，支持windows，linux，android、ios等，使用mavlink协议。

>[【天穹飞控】QGroudControl地面站使用教程](http://bbs.loveuav.com/thread-11450-1-1.html)

![QGroudControl](https://github.com/loveuav/BlueSkyFlightControl/blob/master/PIC/QGroudControl.jpg)

## 作者相关
BlueSky

QQ:352707983

## 【深入浅出多旋翼飞控开发】
本人以个人的一些浅陋经验，结合本飞控项目，编写的一系列教程，持续更新中。

教程地址：http://bbs.loveuav.com/thread-11317-1-1.html

目录

[序：我的多旋翼飞控学习历程](http://bbs.loveuav.com/thread-11316-1-1.html)

[概述篇：一.多旋翼飞控发展史](http://bbs.loveuav.com/thread-693-1-1.html)

[概述篇：二.多旋翼飞控技术综述](http://bbs.loveuav.com/thread-11308-1-1.html)

[预备篇：一.元器件选型及飞控电路设计](http://bbs.loveuav.com/thread-11314-1-1.html)

预备篇：二.Altium Designer的使用

预备篇：三.飞行器组装

[预备篇：四.飞控代码下载与编译](http://bbs.loveuav.com/thread-11422-1-1.html)

预备篇：五.单片机开发及RTOS移植

预备篇：六.外设驱动开发

预备篇：七.传感器驱动开发

初级篇：一.关于姿态估计

初级篇：二.传感器的简单校准

初级篇：三.欧拉角与方向余弦矩阵

初级篇：四.互补滤波

初级篇：五.卡尔曼滤波

初级篇：六.四元数

初级篇：七.以传感器恒温为例学习PID控制

初级篇：八.多旋翼控制模型简析

初级篇：九.多旋翼姿态控制

中级篇：一.数字低通滤波器

中级篇：二.串级PID控制算法

中级篇：三.垂直飞行速度及高度估计

中级篇：四.GPS数据解析和坐标转换

中级篇：五.水平飞行速度及位置估计

中级篇：六.飞行速度与位置控制

中级篇：七.自动返航功能的实现

高级篇：一.基于椭球拟合的传感器校准

高级篇：二.传感器的安装误差校准

高级篇：三.圆周飞行中的向心加速度误差补偿

高级篇：四.兴趣点环绕飞行

高级篇：五.自动航线飞行

高级篇：六.飞控故障与传感器质量检测

高级篇：七.飞行状态分类

高级篇：八.起飞与落地检测

进阶篇：一.机体震动对飞控导航计算和控制的影响分析

进阶篇：二.飞行过程中姿态估计的动态精度优化

进阶篇：三.陀螺仪与加速度计的零偏误差实时估计

进阶篇：四.基于飞行状态误差模型的自适应融合算法在组合导航中的应用
