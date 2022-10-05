# 适用于RM2100且带有华工校园网客户端的Padavan及OpenWrt固件
> ## 自己编译固件的原因：
>  * 在使用scutclient的同时对ssr之类的工具有需求，在网上找不到兼顾两种需求的固件，于是自己动手编译
> ## 最近更新时间：2022-9-29

# [openwrt编译教程](./openwrt_build.md)
----------------------------------
# 已发布版本--见[release](https://github.com/chengqingtan/Padavan-build-RM2100/releases)：
> ## [v3.0](https://github.com/chengqingtan/Padavan-build-RM2100/releases/tag/v3.0)
>  * Padavan 和 Lean OpenWrt 固件
>  * 如果只想上校园网，那就推荐使用Padavan，有图形界面、配置简单，但Padavan里的SSR-Plus无法使用
>  * Lean OpenWrt固件存在重启后配置丢失的bug
> ## [v3.1](https://github.com/chengqingtan/Padavan-build-RM2100/releases/tag/v3.1)
>  * Lienol OpenWrt 固件
>  * 编译了scutclient，但没有图形界面
>  * 没有Lean OpenWrt重启后配置丢失的bug
> ## [v4.0](https://github.com/chengqingtan/Padavan-build-RM2100/releases/tag/v4.0)
>  * Lienol OpenWrt 固件
>  * 编译了luci-app-scutclient，这一版本有了图形界面，配置也很简单
> ## [v4.1](https://github.com/chengqingtan/Padavan-build-RM2100/releases/tag/v4.1)
>  * 将 Lienol OpenWrt 固件版本更新到 22.03-snapshot
> ## 目前推荐的是 [v3.0 Padavan纯净版](https://github.com/chengqingtan/Padavan-build-RM2100/releases/download/v3.0/padavan_scut.zip) 和 [v4.1 Lienol ssr-plus版本]>(https://github.com/chengqingtan/Padavan-build-RM2100/releases/download/v4.1/lienol22.03-scutUI-ssr.zip)

# Padavan 自动编译工作流：
    build-padavan 编译4.4内核的Padavan固件
  ## 如何开始编译：（以下三种方式任选其一，记得先fork到自己的存储库中）
    (1)点击star
    (2)发布新的release
    (3)在workflow里点击Build Padavan 4.4并Run workflow
* 编译4.4内核版本的原因：本人在使用3.4内核的Padavan固件进管理后台经常卡顿
* 4.4内核版本的不足：无法通过编译napt66的方式来使用IPv6（但有其他替代方案，见 [release v3.0](https://github.com/chengqingtan/Padavan-build-RM2100/releases/tag/v3.0)）
