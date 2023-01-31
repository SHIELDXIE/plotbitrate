# PlotBitrate 中文使用文档

## 简介

这是一个调用ffprobe对音视频流进行分析的python 脚本。通过调用ffprobe抓取音视频流每一帧的码率和帧类型信息，生成 .xml 的元数据信息；调用Matplotlib 绘制可视化图表，生成包含峰值码率、平均码率、帧类型的图表图像。



## 输出文件类型

元数据文件 ( .csv .xml )

图表图像 ( .eps .jpg .pdf .pgf .png .ps .raw .svg .tiff .webp )



## 安装

```powershell
pip install plotbitrate
```



## 使用

```powershell
positional arguments:
  INPUT                 input file/stream

options:
  -h, --help            show this help message and exit
  --version             show program's version number and exit
  -s {audio,video}, --stream {audio,video}
                        Stream type (default: video)
  -o OUTPUT, --output OUTPUT
                        Output file
  -f {eps,jpg,jpeg,pdf,pgf,png,ps,raw,rgba,svg,svgz,tif,tiff,webp,xml_raw,csv_raw}, --format {eps,jpg,jpeg,pdf,pgf,png,ps,raw,rgba,svg,svgz,tif,tiff,webp,xml_raw,csv_raw}
                        Output file format
  --no-progress         Hides progress
  --min MIN             Set plot minimum (kbps)
  --max MAX             Set plot maximum (kbps)
  -t, --show-frame-types
                        Show bitrate of different frame types
  -d, --downscale       Enable downscaling of values, so that the visible level of detail in the graph is reduced and
                        rendered faster. This is useful if the video is very long and an overview of the bitrate
                        fluctuation is sufficient.
  --max-display-values MAX_DISPLAY_VALUES
                        If downscaling is enabled, set the maximum number of values shown on the x axis. Will
                        downscale if video length is longer than the given value. Will not downscale if set to -1. Not
                        compatible with option --show-frame-types (default: 700)
```

### 示例

1.以图表方式在窗口中显示视频流的码率信息

```powershell
plotbitrate input.mkv
```

2.以图表方式在窗口中显示视频流每个帧类型的码率信息

```powershell
plotbitrate -t input.mkv
```

3.以图表方式在窗口中显示音频流的码率信息

```powershell
plotbitrate -s audio input.mkv
```

4.将ffprobe 解析的元数据输出为 .xml文件

```powershell
plotbitrate -f xml_raw -o frames.xml input.mkv
```

5.绘制xml 元数据的图表

```powershell
plotbitrate frames.xml
```
