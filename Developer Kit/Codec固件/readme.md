
## ISD9160使用说明
### Overview
* ISD9160是一块在Developerkit单板上的codec芯片。该芯片拥有本地语音识别和播放录音的能力，它与MCU使用I2C和I2S总线进行通讯，其中同步控制信息和固件升级数据走I2C，音频数据走I2S。在Developerkit单板出厂时已经为ISD9160预烧录了一份固件，这份固件仅支持本地音频回环和固件升级功能。

* 升级版本号有固定的格式，分为主版本号和子版本号。主版本号用于区分版本功能，子版本号用于标记版本新旧程度。
* 不同的主版本可以直接升级，例如：可以从v1.01升级到v2.01，也可从v2.01升级到v1.01。
* 当主版本号相同时，升级固件版本号低于或等于当前运行的版本号，无法进行升级操作，例如：可以从v2.00升级到v2.01，但不可从v2.01升级到v2.00。

## 相关主版本功能说明：

* v1.xx-------录音保存和播放音频功能
* v2.xx-------本地语音识别功能

## 按键功能说明：
* B键---------升级isd9160固件
* M键---------录音
* A键---------播放

## 操作步骤

* 1 . 将待升级的isd9160固件复制到SD卡中，重命名为：isd9160_fw.bin。并将SD卡插入Developerkit的SD卡槽中
* 2 . 编译developerkitaudio@developerkit
* 3 . 将编译生成的developerkitaudio@developerkit.bin，烧录进开发板中
* 4 . 给开发板重新上电，并打开串口调试工具
* 5 . 按B键升级isd9160固件，LED3灯点亮，串口打印升级信息。没有报错误信息打印同时LED3灯闪烁两下，则表示升级成功
* 6 . 使用v1.01版本时，按M键开始录音，LED1灯点亮；再次按下M键结束录音，LED1灯闪烁两下。插入耳机，按A键播放录音，LED2灯点亮；LED2灯闪烁两下，表示录音播放完毕。
* 7 . 使用v2.01版本时，对着麦克风说：“小特小特”，唤醒设备，LED1将会亮10秒，这时可尝试说本文末尾的短语。设备识别到设定的短语时，LED2灯会闪烁两下。若在设备唤醒的10秒内未识别到语句，LED1灯熄灭，需要再次唤醒才可使用。


## version update record:

---- v1.01 ----

* v1.xx初版，功能包含版本信息同步、版本升级、录音(I2S)、播放(I2S)

---- v1.02 ----

* 解决了概率性录音有杂音的问题

---- v2.01 ----

* v2.xx初版，功能包含版本信息同步、版本升级、语音识别。支持的短语列表如下:
	0. 小特小特
	1. 拍照
	2. 扫一扫
	3. 音乐播放
	4. 音乐暂停
	5. 上一首
	6. 下一首
	7. 音量增大
	8. 音量减小
	9. 当前温度
	10. 当前湿度
	11. 请开灯
	12. 请关灯
