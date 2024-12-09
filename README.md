# STM32F103学习笔记（5）——数码管驱动TM1650使用

## 概述

本文档提供了关于如何使用STM32F103系列微控制器配合TM1650集成电路驱动数码管的详细教程。TM1650是一个集成了I2C接口的LED驱动控制芯片，特别适合驱动四位数码管显示，并具备键盘扫描功能。本教程适合嵌入式开发者，特别是那些正在学习STM32F103平台下的硬件驱动编程的读者。

## 硬件要求

- STM32F103开发板
- TM1650四路数码管驱动模块
- 接线材料（杜邦线等）

## 核心知识点

- **TM1650特性**：支持8段×4位和7段×4位显示模式，具有亮度调节，内置I2C接口，工作电压范围宽。
- **硬件连接**：明确STM32与TM1650之间的具体引脚连接，如SCL连接PB6，SDA连接PB5。
- **I2C驱动**：在FreeRTOS环境下配置模拟I2C通讯，实现STM32与TM1650的数据交换。
- **驱动程序编写**：创建`board_i2c.c/h`, `board_tm1650.c/h`等文件，编写初始化、写显存、显示设置与显示数字的函数。

## 示例代码概览

- **初始化**：确保包含了必要的头文件，并配置好I2C模拟接口。
- **TM1650驱动函数**：
    - `TM1650_Write(addr, data)` 用于写入显存。
    - `TM1650_SetDisplay(brightness, mode, state)` 控制显示亮度和开关。
    - `TM1650_SetNumber(index, mode, num)` 设置特定位置的数字显示。

## 使用步骤

1. **硬件连线**：根据引脚图完成STM32与TM1650的物理连接。
2. **软件准备**：在项目中添加所需的源代码文件，并确保已正确配置I2C通信。
3. **编译与烧录**：在IDE中编译工程并通过ST-Link等工具烧录至STM32。
4. **测试**：运行程序，验证数码管是否按照预期显示数字，调整不同模式和亮度。

## 注意事项

- 在移植过程中可能遇到的`common.h`文件错误，可以通过替换为`uint8_t`或`unsigned char`解决。
- 实验前，确保理解I2C通信协议的基础知识，以更好地调试代码。

通过跟随这篇教程，你可以学会如何有效地利用STM32F103控制TM1650，进而驱动数码管，这对于学习嵌入式系统的硬件控制和通信是非常有益的实践。

## 下载链接

[STM32F103学习笔记5数码管驱动TM1650使用](https://pan.quark.cn/s/794a3e0307a3)