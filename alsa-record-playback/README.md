
要编译和运行这个程序，你需要：

1. 确保已安装 ALSA 开发库：
```bash
sudo apt-get install libasound2-dev
```

2. 编译程序：
```bash
mkdir build
cd build
cmake ..
make
```

3. 运行程序：
```bash
./record
```

程序运行后，会开始录制音频，按 Ctrl+C 可以停止录制。录制的 PCM 数据将保存在 `recording.pcm` 文件中。

需要注意的是：
1. 录制的 PCM 数据是 16 位有符号小端格式
2. 默认使用系统默认音频设备，如果需要使用特定设备，可以修改代码中的 `device` 变量
3. 如果需要修改采样率或通道数，可以修改相应的参数

你可以使用以下命令来播放录制的 PCM 文件：
```bash
aplay -f S16_LE -r 44100 -c 2 recording.pcm
```
或者
```
ffplay -f s16le -ar 44100 -ac 2 recording.pcm
```

 