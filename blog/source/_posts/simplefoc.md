---
title: simplefoc
date: 2022-10-22 08:58:55
tags:
categories:
---


# 项目资料收集

| simplef foc软件库 | Arduino-FOC             | https://github.com/simplefoc/Arduino-FOC             |
| ----------------- | ----------------------- | ---------------------------------------------------- |
| PCB工程           | Arduino-SimpleFOCShield | https://github.com/simplefoc/Arduino-SimpleFOCShield |

硬件数据手册

| INA240       | 电流检测放大器 |
| ------------ | -------------- |
| L78M08       | 稳压器         |
| L6234PD013TR | 三相电机驱动器 |



| 驱动板淘宝购买链接 | https://item.taobao.com/item.htm?spm=a1z09.2.0.0.255e2e8dcrGLst&id=642985271177&_u=h2p6t0m7c0b1 |
| ------------------ | ------------------------------------------------------------ |
| CSDN教程           | https://blog.csdn.net/gjy_skyblue/category_10936827.html?spm=1001.2014.3001.5482 |
| github仓库地址     | https://github.com/makerbase-mks/simplefoc-MKS               |

# 驱动板到手测试

直流电源24V

硬件配置如下:

1.  simple foc驱动板
2.  电机一个

## 开环位置控制

运行第一个示例open_loop_position_example

修改参数如下

BLDCMotor motor = BLDCMotor(7);

driver.voltage_power_supply = 24;

motor.voltage_limit = 1;

选择串口

输入T6.28,或者其他位置参数，观察到电机运行在不同的位置

## 开环速度控制

运行第二个示例open_loop_velocity_example

修改参数如上个示例

串口输入信息T5,或者其他速度参数，观察电机以一定速度运行

## 模拟量测量速度和位置

AS5600传感器Analog接口测试

<img src="https://cdn.jsdelivr.net/gh/czc13611858691/picgoRepo@master/20221022084518.jpg" alt="在这里插入图片描述" style="zoom:25%;" />

红色5V/黑色GND/黄色A1

文件 -> 示例-> Simple FOC -> utils -> sensor_test -> magnetic_sensors -> magnetic_sensor_analog_example

串口打印速度和位置信息，用手转动电机可以观察到信息变化

## I2C传输速度和位置信息

I2C接线如下图

<img src="https://cdn.jsdelivr.net/gh/czc13611858691/picgoRepo@master/20221022084737.jpg">

红色5V/黑色GND/黄色SDA/红色SCL

运行示例 工程文件->示例-> Simple FOC -> utils -> sensor_test -> magnetic_sensors -> magnetic_sensor_i2c_example，测试效果类似上一个例程



## 闭环位置控制

运行闭环位置测试文件 -> 示例 -> Simple FOC -> motion_control -> position_motion_control -> magnetic_sensor -> angle_control

根据选择的模拟量接口或者I2C接口，取消注释

修改参数

```
BLDCMotor motor = BLDCMotor(7);
driver.voltage_power_supply = 24;
motor.PID_velocity.I = 2;
motor.voltage_limit = 1;
```

上传代码，串口输出调试信息

输入T6.28，观察电机转一圈 2pi

松手后电机会回到原位置，这就是闭环电机

注意有以下问题:

-   电机异常抖动



## 闭环速度控制

闭环速度测试

文件 -> 示例 -> Simple FOC -> motion_control -> velocity_motion_control -> magnetic_sensor -> velocity_control

修改参数同上个例程

输入T2,固定速度转动

## 电流传感器测试

电流传感器测试

angle_control_current_sense_test.ino

上传代码后可以通过串口观察4个参数返回，分别为

1.  A相电流
2.  B相电流
3.  未知
4.  幅值

# 硬件部分学习

## 稳压器L78M08

<img src="https://cdn.jsdelivr.net/gh/czc13611858691/picgoRepo@master/20221022085011.png"/>

![](https://cdn.jsdelivr.net/gh/czc13611858691/picgoRepo@master/20221022085018.png)

![](https://cdn.jsdelivr.net/gh/czc13611858691/picgoRepo@master/20221022085025.png)

-   输入电压10.5V-23V
-   输出电压8V

## 电流放大器

## 三相电机驱动

# 软件部分学习

## c++虚函数

BLDCDriver3PWM.h文件中出现了虚函数

```
virtual void setPhaseState(int sa, int sb, int sc) override;
```

虚函数的概念:

虚函数是指一个类中你希望重载的成员函数 ，当你用一个  基类指针或引用  指向一个继承类对象的时候，调用一个虚函数时, 实际调用的是继承类的版本。

```
class BLDCDriver{
	...
	virtual void setPhaseState(int sa, int sb, int sc) = 0;
	...
};
```

```
class BLDCDriver3PWM: public BLDCDriver{
	...
	virtual void setPhaseState(int sa, int sb, int sc) override;
	...
}
```

由上图示例可以发现BLDCDriver3PWM继承自BLDCDriver,setPhaseState函数在两个类中都进行了定义，实际调用这个函数的时候，调用的是BLDCDriver3PWM中的。