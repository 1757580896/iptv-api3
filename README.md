<div align="center">
  <img src="./static/images/logo.png" alt="logo"/>
  <h1 align="center">IPTV-API</h1>
</div>

<div align="center">一个可高度自定义的IPTV接口更新项目📺，自定义频道菜单，自动获取直播源，测速验效后生成可用的结果，可实现『✨秒播级体验🚀』</div>
<br>
<p align="center">
  <a href="https://github.com/Guovin/iptv-api/releases/latest">
    <img src="https://img.shields.io/github/v/release/guovin/iptv-api" />
  </a>
  <a href="https://www.python.org/">
    <img src="https://img.shields.io/badge/python-%20%3D%203.13-47c219" />
  </a>
  <a href="https://github.com/Guovin/iptv-api/releases/latest">
    <img src="https://img.shields.io/github/downloads/guovin/iptv-api/total" />
  </a>
  <a href="https://hub.docker.com/repository/docker/guovern/iptv-api">
    <img src="https://img.shields.io/docker/pulls/guovern/iptv-api" />
  </a>
  <a href="https://github.com/Guovin/iptv-api/fork">
    <img src="https://img.shields.io/github/forks/guovin/iptv-api" />
  </a>
</p>

[English](./README_en.md) | 中文

- [✅ 特点](#特点)
- [🔗 最新结果](#最新结果)
- [⚙️ 配置参数](#配置)
- [🚀 快速上手](#快速上手)
    - [工作流](#工作流)
    - [命令行](#命令行)
    - [GUI软件](#GUI-软件)
    - [Docker](#Docker)
- [📖 详细教程](./docs/tutorial.md)
- [🗓️ 更新日志](./CHANGELOG.md)
- [❤️ 赞赏](#赞赏)
- [👀 关注(更新订阅+答疑交流)](#关注)
- [📣 免责声明](#免责声明)
- [⚖️ 许可证](#许可证)

📍订阅源来自：

- [iptv-org/iptv](https://github.com/iptv-org/iptv)
- [suxuang/myIPTV](https://github.com/suxuang/myIPTV)
- [kimwang1978/collect-tv-txt](https://github.com/kimwang1978/collect-tv-txt)
- [xzw832/cmys](https://github.com/xzw832/cmys)
- [asdjkl6/tv](https://github.com/asdjkl6/tv)
- [yuanzl77/IPTV](https://github.com/yuanzl77/IPTV)
- [fanmingming/live](https://github.com/fanmingming/live)
- [vbskycn/iptv](https://github.com/vbskycn/iptv)
- [YueChan/Live](https://github.com/YueChan/Live)
- [YanG-1989/m3u](https://github.com/YanG-1989/m3u)

📍频道图标来自：

- [fanmingming/live](https://github.com/fanmingming/live)

## 特点

- ✅ 自定义模板，生成您想要的频道
- ✅ 支持多种获取源方式：本地源、组播源、酒店源、订阅源、关键字搜索
- ✅ 接口测速验效，获取延迟、速率、分辨率，过滤无效接口
- ✅ 偏好设置：IPv4、IPv6、接口来源排序优先级与数量配置、接口白名单
- ✅ 定时执行，北京时间每日 6:00 与 18:00 执行更新
- ✅ 支持多种运行方式：工作流、命令行、GUI 软件、Docker(amd64/arm64/arm v7)
- ✨ 更多功能请见[配置参数](#配置)

## 最新结果

- 接口源：

```bash
https://ghproxy.cc/https://raw.githubusercontent.com/Guovin/iptv-api/gd/output/result.m3u
```

```bash
https://ghproxy.cc/https://raw.githubusercontent.com/Guovin/iptv-api/gd/output/result.txt
```

🙏 感谢由[ghproxy.cc](https://ghproxy.cc)提供的代理加速服务

或

```bash
https://cdn.jsdelivr.net/gh/Guovin/iptv-api@gd/output/result.m3u
```

```bash
https://cdn.jsdelivr.net/gh/Guovin/iptv-api@gd/output/result.txt
```

- 数据源：

```bash
https://ghproxy.cc/https://raw.githubusercontent.com/Guovin/iptv-api/gd/source.json
```

或

```bash
https://cdn.jsdelivr.net/gh/Guovin/iptv-api@gd/source.json
```

## 配置

| 配置项                    | 描述                                                                                                                                                                    | 默认值               |
|:-----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------|
| open_driver            | 开启浏览器运行，若更新无数据可开启此模式，较消耗性能                                                                                                                                            | False             |
| open_empty_category    | 开启无结果频道分类，自动归类至底部                                                                                                                                                     | False             |
| open_filter_resolution | 开启分辨率过滤，低于最小分辨率（min_resolution）的接口将会被过滤，GUI用户需要手动安装FFmpeg，程序会自动调用FFmpeg获取接口分辨率，推荐开启，虽然会增加测速阶段耗时，但能更有效地区分是否可播放的接口                                                      | True              |
| open_filter_speed      | 开启速率过滤，低于最小速率（min_speed）的接口将会被过滤                                                                                                                                      | True              |
| open_hotel             | 开启酒店源功能，关闭后所有酒店源工作模式都将关闭                                                                                                                                              | True              |
| open_hotel_foodie      | 开启 Foodie 酒店源工作模式                                                                                                                                                     | True              |
| open_hotel_fofa        | 开启 FOFA、ZoomEye 酒店源工作模式                                                                                                                                               | True              |
| open_keep_all          | 开启保留所有检索结果，会保留非模板频道名称的结果，推荐手动维护时开启                                                                                                                                    | False             |
| open_local             | 开启本地源功能，将使用模板文件与本地源文件中的数据                                                                                                                                             | True              |
| open_m3u_result        | 开启转换生成 m3u 文件类型结果链接，支持显示频道图标                                                                                                                                          | True              |
| open_multicast         | 开启组播源功能，关闭后所有组播源工作模式都将关闭                                                                                                                                              | True              |
| open_multicast_foodie  | 开启 Foodie 组播源工作模式                                                                                                                                                     | True              |
| open_multicast_fofa    | 开启 FOFA 组播源工作模式                                                                                                                                                       | True              |
| open_online_search     | 开启关键字搜索源功能                                                                                                                                                            | False             |
| open_proxy             | 开启代理，自动获取免费可用代理，若更新无数据可开启此模式                                                                                                                                          | False             |
| open_request           | 开启查询请求，数据来源于网络（仅针对酒店源与组播源）                                                                                                                                            | False             |
| open_service           | 开启页面服务，用于控制是否启动结果页面服务；如果使用青龙等平台部署，有专门设定的定时任务，需要更新完成后停止运行，可以关闭该功能                                                                                                      | True              |
| open_sort              | 开启排序功能（响应速度、日期、分辨率）                                                                                                                                                   | True              |
| open_subscribe         | 开启订阅源功能                                                                                                                                                               | False             |
| open_update            | 开启更新，用于控制是否更新接口，若关闭则所有工作模式（获取接口和测速）均停止                                                                                                                                | True              |
| open_update_time       | 开启显示更新时间                                                                                                                                                              | True              |
| open_url_info          | 开启显示接口说明信息，用于控制是否显示接口来源、分辨率、协议类型等信息，为$符号后的内容，播放软件使用该信息对接口进行描述，若部分播放器（如PotPlayer）不支持解析导致无法播放可关闭                                                                        | False             |
| open_use_cache         | 开启使用本地缓存数据，适用于查询请求失败场景（仅针对酒店源与组播源）                                                                                                                                    | True              |
| open_history           | 开启使用历史更新结果（包含模板与结果文件的接口），合并至本次更新中                                                                                                                                     | True              |
| app_port               | 页面服务端口，用于控制页面服务的端口号                                                                                                                                                   | 8000              |
| final_file             | 生成结果文件路径                                                                                                                                                              | output/result.txt |
| hotel_num              | 结果中偏好的酒店源接口数量                                                                                                                                                         | 10                |
| hotel_page_num         | 酒店地区获取分页数量                                                                                                                                                            | 1                 |
| hotel_region_list      | 酒店源地区列表，"全部"表示所有地区                                                                                                                                                    | 全部                |
| ipv4_num               | 结果中偏好的 IPv4 接口数量                                                                                                                                                      | 5                 |
| ipv6_num               | 结果中偏好的 IPv6 接口数量                                                                                                                                                      | 5                 |
| ipv6_support           | 强制认为当前网络支持IPv6，跳过检测                                                                                                                                                   | False             |
| ipv_type               | 生成结果中接口的协议类型，可选值：ipv4、ipv6、全部、all                                                                                                                                     | 全部                |
| ipv_type_prefer        | 接口协议类型偏好，优先将该类型的接口排在结果前面，可选值：ipv4、ipv6、自动、auto                                                                                                                        | 自动                |
| local_file             | 本地源文件路径                                                                                                                                                               | config/local.txt  |
| local_num              | 结果中偏好的本地源接口数量                                                                                                                                                         | 10                |
| min_resolution         | 接口最小分辨率，需要开启 open_filter_resolution 才能生效                                                                                                                              | 1920x1080         |
| min_speed              | 接口最小速率（单位M/s），需要开启 open_filter_speed 才能生效                                                                                                                             | 0.2               |
| multicast_num          | 结果中偏好的组播源接口数量                                                                                                                                                         | 10                |
| multicast_page_num     | 组播地区获取分页数量                                                                                                                                                            | 1                 |
| multicast_region_list  | 组播源地区列表，"全部"表示所有地区                                                                                                                                                    | 全部                |
| online_search_num      | 结果中偏好的关键字搜索接口数量                                                                                                                                                       | 0                 |
| online_search_page_num | 关键字搜索频道获取分页数量                                                                                                                                                         | 1                 |
| origin_type_prefer     | 结果偏好的接口来源，结果优先按该顺序进行排序，逗号分隔，例如：local,hotel,multicast,subscribe,online_search；local：本地源，hotel：酒店源，multicast：组播源，subscribe：订阅源，online_search：关键字搜索；不填写则表示不指定来源，按照接口速率排序 |                   |
| recent_days            | 获取最近时间范围内更新的接口（单位天），适当减小可避免出现匹配问题                                                                                                                                     | 30                |
| request_timeout        | 查询请求超时时长，单位秒(s)，用于控制查询接口文本链接的超时时长以及重试时长，调整此值能优化更新时间                                                                                                                   | 10                |
| sort_timeout           | 单个接口测速超时时长，单位秒(s)；数值越大测速所属时间越长，能提高获取接口数量，但质量会有所下降；数值越小测速所需时间越短，能获取低延时的接口，质量较好；调整此值能优化更新时间                                                                             | 10                |
| source_file            | 模板文件路径                                                                                                                                                                | config/demo.txt   |
| subscribe_num          | 结果中偏好的订阅源接口数量                                                                                                                                                         | 10                |
| time_zone              | 时区，可用于控制更新时间显示的时区，可选值：Asia/Shanghai 或其它时区编码                                                                                                                           | Asia/Shanghai     |
| urls_limit             | 单个频道接口数量                                                                                                                                                              | 10                |
| update_time_position   | 更新时间显示位置，需要开启 open_update_time 才能生效，可选值：top、bottom，top: 显示于结果顶部，bottom: 显示于结果底部                                                                                       | top               |

## 快速上手

### 工作流

Fork 本项目并开启工作流更新，具体步骤请见[详细教程](./docs/tutorial.md)

### 命令行

```shell
pip install pipenv
```

```shell
pipenv install --dev
```

启动更新：

```shell
pipenv run dev
```

启动服务：

```shell
pipenv run service
```

### GUI 软件

1. 下载[IPTV-API 更新软件](https://github.com/Guovin/iptv-api/releases)，打开软件，点击更新，即可完成更新

2. 或者在项目目录下运行以下命令，即可打开 GUI 软件：

```shell
pipenv run ui
```

<img src="./docs/images/ui.png" alt="IPTV-API更新软件" title="IPTV-API更新软件" style="height:600px" />

### Docker

- iptv-api（完整版本）：性能要求较高，更新速度较慢，稳定性、成功率高；修改配置 open_driver = False 可切换到 Lite
  版本运行模式（推荐酒店源、组播源、关键字搜索使用此版本）
- iptv-api:lite（精简版本）：轻量级，性能要求低，更新速度快，稳定性不确定（推荐订阅源使用此版本）

1. 拉取镜像：

- iptv-api：

```bash
docker pull guovern/iptv-api:latest
```

🚀 代理加速（推荐国内用户使用）：

```bash
docker pull docker.1ms.run/guovern/iptv-api:latest
```

- iptv-api:lite：

```bash
docker pull guovern/iptv-api:lite
```

🚀 代理加速（推荐国内用户使用）：

```bash
docker pull docker.1ms.run/guovern/iptv-api:lite
```

2. 运行容器：

- iptv-api：

```bash
docker run -d -p 8000:8000 guovern/iptv-api
```

- iptv-api:lite：

```bash
docker run -d -p 8000:8000 guovern/iptv-api:lite
```

卷挂载参数（可选）：
实现宿主机文件与容器文件同步，修改模板、配置、获取更新结果文件可直接在宿主机文件夹下操作

以宿主机路径/etc/docker 为例：

- iptv-api：

```bash
docker run -v /etc/docker/config:/iptv-api/config -v /etc/docker/output:/iptv-api/output -d -p 8000:8000 guovern/iptv-api
```

- iptv-api:lite：

```bash
docker run -v /etc/docker/config:/iptv-api-lite/config -v /etc/docker/output:/iptv-api-lite/output -d -p 8000:8000 guovern/iptv-api:lite
```

端口环境变量：

```bash
-e APP_PORT=8000
```

3. 更新结果：

- 接口地址：`ip:8000`
- m3u 接口：`ip:8000/m3u`
- txt 接口：`ip:8000/txt`
- 接口内容：`ip:8000/content`
- 测速日志：`ip:8000/log`

## 更新日志

[更新日志](./CHANGELOG.md)


## 免责声明

本项目仅供学习交流用途，接口数据均来源于网络，如有侵权，请联系删除

## 许可证

[MIT](./LICENSE) License &copy; 2024-PRESENT [Govin](https://github.com/guovin)

## 项目结构

```
.
├── .github/workflows/          # GitHub Actions 工作流配置
│   ├── main.yml               # IPTV源更新工作流
│   ├── docker-build.yml       # Docker镜像构建工作流  
│   └── release.yml            # 版本发布工作流
├── config/                     # 配置文件目录
│   ├── config.ini             # 主配置文件
│   ├── demo.txt               # 频道模板文件
│   ├── local.txt              # 本地源配置
│   ├── subscribe.txt          # 订阅源配置
│   ├── whitelist.txt          # 白名单配置
│   └── blacklist.txt          # 黑名单配置
├── utils/                      # 工具类目录
│   ├── channel.py             # 频道处理模块
│   ├── speed.py               # 速度测试模块
│   └── tools.py               # 通用工具模块
├── output/                     # 输出目录
│   ├── result.m3u             # M3U格式结果
│   └── result.txt             # 文本格式结果
├── requirements.txt           # Python依赖配置
├── main.py                    # 主程序入口
└── activate.sh                # 虚拟环境激活脚本
```

## 工作流说明

### 1. main.yml - IPTV源更新工作流
- 触发条件：
  - 定时触发：每天北京时间14:00和02:00
  - 支持手动触发
- 主要功能：
  - 安装Python环境和依赖
  - 更新IPTV源
  - 自动提交更新结果

### 2. docker-build.yml - Docker镜像构建工作流
- 触发条件：
  - Dockerfile或requirements.txt变更时
  - 支持手动触发
- 主要功能：
  - 构建多平台Docker镜像(amd64/arm64)
  - 推送镜像到Docker Hub
  - 维护latest和版本标签

### 3. release.yml - 版本发布工作流
- 触发条件：
  - 推送版本标签(v*)时
  - 支持手动触发并指定版本
- 主要功能：
  - 打包项目文件
  - 创建GitHub Release
  - 上传发布包

## 配置文件说明

### 1. config.ini
主配置文件，包含所有可配置项：
- 功能开关配置
- 接口数量限制
- 测速参数设置
- 服务端口配置
- 时区设置等

### 2. demo.txt
频道模板文件，定义需要获取的频道列表：
- 频道分类
- 频道名称
- 频道排序

### 3. local.txt
本地源配置文件：
- 自定义IPTV源
- 支持设置白名单
- 一行一个源

### 4. subscribe.txt
订阅源配置文件：
- 远程M3U8播放列表
- 支持代理加速
- 一行一个订阅

### 5. whitelist.txt
白名单配置：
- 可信IPTV流列表
- 优先处理且不过滤
- 支持按频道名过滤

### 6. blacklist.txt
黑名单配置：
- 禁止的IPTV流列表
- 自动过滤匹配的流
- 支持关键字匹配

## 核心模块说明

### 1. speed.py
速度测试模块：
- M3U8流测试
- 下载速度测量
- 流分辨率检测
- 基于FFmpeg的流分析
- 速度测试结果缓存

### 2. channel.py
频道处理模块：
- 频道解析
- 模板匹配
- 源聚合
- 结果生成

### 3. tools.py
通用工具模块：
- 网络请求
- 文件操作
- 缓存管理
- 日志记录
