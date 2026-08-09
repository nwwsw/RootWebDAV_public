# RootWebDAV 1.0.1（发布二进制）

本仓库仅存放 RootWebDAV 的发布二进制（APK 与 Magisk 模块）。

## 文件

- `RootWebDAVController-1.0.1-aligned-signed.apk`：控制 APK（包名 `com.nwwsw.rootwebdav`）
- `RootWebDAV-Backend-v1.0.1.zip`：Magisk / KernelSU / APatch 模块
- `SHA256SUMS.txt`：上述文件的 SHA-256 校验值

## 安装

1. 安装模块：在 Magisk / KernelSU / APatch 中刷入 `RootWebDAV-Backend-v1.0.1.zip`，然后重启；
2. 安装 APK：`adb install RootWebDAVController-1.0.1-aligned-signed.apk` 或直接打开安装；
3. 在系统快捷设置中添加“RootWebDAV”磁贴；
4. 打开控制页设置共享目录与密码（默认值见下），点击磁贴即可启停 WebDAV。

## 工作方式

本模块可以让手机作为 WebDAV 服务器运行。其他设备与手机连接同一个 Wi-Fi，或者连接该手机开启的热点时，可以通过手机当前的局域网 IP 地址和 WebDAV 端口访问共享文件。

APK 本身不提供 WebDAV 服务，只用于修改 WebDAV 配置；真正监听端口并提供 WebDAV 功能的是刷入手机的模块。修改配置后不会自动重新加载，必须手动重启 WebDAV（先停止再启动），新配置才会生效。

## 默认值

- 用户名：`nwwsw`
- 密码：`12345678`（长度最短为8位字符）
- 共享目录：`/storage/emulated/0/Download`
- 端口：`8080`

## 功能

- 磁贴一键启停 WebDAV，带通知栏提示；
- 控制 APK 优先通过 App 私有 Unix socket 直连模块（不经过 su），失败自动回退；
- 支持开机自启。
