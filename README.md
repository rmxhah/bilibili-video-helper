# B站视频助手

> B站视频/字幕/音频下载工具，扫码登录即用，支持4K全画质

## 功能

- 🔐 **扫码登录** — 打开程序→手机B站App扫码→完成，无需手动配置
- 📝 **字幕下载** — SRT + 纯文本，原生CC字幕优先，AI字幕兜底
- 🎵 **音频下载** — 直取DASH最高码率音频流 (.m4a)
- 🎬 **视频下载** — DASH全画质可选 (4K/1080P/720P...)，内置ffmpeg合并
- ⚡ **多线程加速** — 4线程分块并行下载

## 快速开始

1. 下载 `B站视频助手.zip` 并解压
2. 双击 `B站视频助手.exe`
3. 点击「扫码登录」→ 手机B站App扫码
4. 粘贴B站视频链接，选择画质和输出类型
5. 点击「开始处理」

## 系统要求

- Windows 10/11 64位
- 无需安装任何依赖

## 工作原理

- 通过B站API获取视频/字幕数据，需要登录态Cookie
- Cookie仅存储在本地 `config.json`，不上传任何服务器
- 视频下载使用DASH协议 + ffmpeg本地合并，支持全部画质

## 隐私说明

- 所有数据仅存储在本地，无任何网络上传
- 扫码登录获取的Cookie保存在 `config.json`，删除此文件即可清除登录
- 分享给他人前请删除 `config.json`

## 构建

```bash
pip install -r requirements.txt
pyinstaller --onedir --name "B站视频助手" \
  --hidden-import bilibili_api --hidden-import bilibili_api.login_v2 \
  --collect-all bilibili_api --noconfirm bilibili_tool_v2.py
```

依赖: `bilibili-api-python`, `requests`, `httpx`, `qrcode`, `Pillow`, `yt-dlp`

ffmpeg需单独放入 `ffmpeg/` 目录。

## License

MIT
