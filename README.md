![GitHub License](https://img.shields.io/github/license/nikkinikki-org/OpenWrt-nikki?style=for-the-badge&logo=github) ![GitHub Tag](https://img.shields.io/github/v/release/nikkinikki-org/OpenWrt-nikki?style=for-the-badge&logo=github) ![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/nikkinikki-org/OpenWrt-nikki/total?style=for-the-badge&logo=github) ![GitHub Repo stars](https://img.shields.io/github/stars/nikkinikki-org/OpenWrt-nikki?style=for-the-badge&logo=github) [![Telegram](https://img.shields.io/badge/Telegram-gray?style=for-the-badge&logo=telegram)](https://t.me/nikkinikki_org)

# Scepter

**注意：本项目是 [Nikki](https://github.com/nikkinikki-org/OpenWrt-nikki) 的一个分支（fork），感谢原项目的贡献者们。**

在OpenWrt上使用Mihomo实现透明代理。

## 前置要求

- OpenWrt >= 23.05
- Linux内核 >= 5.13
- firewall4

## 功能特性

- 透明代理（重定向/TPROXY/TUN，支持IPv4和/或IPv6）
- 访问控制
- 配置文件混合（Profile Mixin）
- 配置文件编辑器
- 定时重启

## 安装与更新

### A. 通过软件源安装（推荐）

1. 添加软件源

```shell
# 只需运行一次
wget -O - https://github.com/nikkinikki-org/OpenWrt-nikki/raw/refs/heads/main/feed.sh | ash
```

2. 安装

```shell
# 可以通过shell或LuCI的`软件`菜单安装
# 使用opkg
opkg install nikki
opkg install luci-app-nikki
opkg install luci-i18n-nikki-zh-cn
# 使用apk
apk add nikki
apk add luci-app-nikki
apk add luci-i18n-nikki-zh-cn
```

### B. 通过发行版安装

```shell
wget -O - https://github.com/nikkinikki-org/OpenWrt-nikki/raw/refs/heads/main/install.sh | ash
```

## 卸载与重置

```shell
wget -O - https://github.com/nikkinikki-org/OpenWrt-nikki/raw/refs/heads/main/uninstall.sh | ash
```

## 使用方法

查看 [Wiki](https://github.com/nikkinikki-org/OpenWrt-nikki/wiki)

## 工作原理

1. 混合并更新配置文件
2. 运行mihomo
3. 设置定时重启
4. 设置IP规则/路由
5. 生成并应用nftables规则

注意：上述步骤可能会根据配置而变化

## 编译

```shell
# 添加软件源
echo "src-git nikki https://github.com/nikkinikki-org/OpenWrt-nikki.git;main" >> "feeds.conf.default"
# 更新并安装软件源
./scripts/feeds update -a
./scripts/feeds install -a
# 编译软件包
make package/luci-app-nikki/compile
```

编译后的软件包文件将位于 `bin/packages/your_architecture/nikki` 目录下。

## 依赖项

- ca-bundle
- curl
- yq
- firewall4
- ip-full
- kmod-inet-diag
- kmod-nft-socket
- kmod-nft-tproxy
- kmod-tun

## 贡献者

[![Contributors](https://contrib.rocks/image?repo=nikkinikki-org/OpenWrt-nikki)](https://github.com/nikkinikki-org/OpenWrt-nikki/graphs/contributors)

## 特别感谢

- [@ApoisL](https://github.com/apoiston)
- [@xishang0128](https://github.com/xishang0128)
