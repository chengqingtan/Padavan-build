# 适用范围：
* 设备为红米AC2100，并对华工校园网客户端scutclient有需求的用户
# 工作流：
* build-padavan 编译4.4内核的Padavan固件
* 如何开始编译：（以下方式选择其一即可）
    (1)点击star
    (2)发布新的release
    (3)在workflow里点击Build Padavan 4.4并Run workflow
    记得先fork到自己的存储库里去哦！
* 编译4.4内核版本的原因：本人在使用3.4内核的Padavan固件进管理后台经常卡顿
* 4.4内核版本的不足：无法通过编译napt66的方式来使用IPv6（但有其他替代方案）
# 已编译固件：
* 已编译的固件发布在release，最新版本为v3.0，编译时间为2022年6月6日
* 同时顺便将近期编译的Lede Openwrt固件一起发布
# 自己编译固件的原因：
* 在使用scutclient的同时对ssr之类的有需求，在网上找不到兼顾两种需求的固件，于是自己动手编译
# 其他注意事项在release v3.0中
