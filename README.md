# ESP32 NTP 时间同步项目

## 项目概述
这是一个基于ESP32的Arduino项目，从WokWi平台下载，主要功能是通过NTP协议获取网络时间并显示在LCD屏幕上。

## 文件结构
```
/root/code/code_esp32/
├── ESP32 NTP Example.ino  # 主程序
├── diagram.json           # 电路图配置
├── libraries.txt          # 依赖库
├── wokwi-project.txt      # 项目来源信息
└── README.md              # 项目说明
```

## 核心功能分析

### 1. WiFi连接
```cpp
const char* ssid = "YOUR_SSID";
const char* password = "YOUR_PASSWORD";
```
- 需要配置WiFi名称和密码
- 用于连接网络获取NTP时间

### 2. NTP时间同步
```cpp
const char* ntpServer = "pool.ntp.org";
const long  gmtOffset_sec = 3600;
const int   daylightOffset_sec = 3600;
```
- 使用pool.ntp.org作为NTP服务器
- GMT偏移量3600秒（1小时）
- 夏令时偏移量3600秒

### 3. LCD显示
```cpp
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);
```
- 使用I2C接口的LCD
- 地址0x27，16列2行

### 4. 主程序流程
- **setup()**: 初始化串口、LCD、WiFi连接、NTP配置
- **loop()**: 每秒获取并显示时间

## 依赖库
- **LiquidCrystal I2C**: 用于控制I2C接口的LCD显示屏

## 电路配置 (diagram.json)
- ESP32开发板
- I2C LCD显示屏（连接到ESP32的I2C引脚）

## 使用说明
1. 修改WiFi凭据（ssid和password）
2. 根据所在时区调整gmtOffset_sec
3. 上传到ESP32开发板
4. LCD将显示当前网络时间

## 特点
- 自动NTP时间同步
- 实时LCD显示
- 串口调试输出
- 支持时区和夏令时配置
