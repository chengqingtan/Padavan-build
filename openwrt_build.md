# 编译openwrt固件

## 用到的源码仓库：

- [lienol openwrt](https://github.com/Lienol/openwrt)
- [openwrt常用软件包](https://github.com/kenzok8/openwrt-packages)
- [scutclient](https://github.com/scutclient/scutclient)
- [luci-app-scutclient](https://github.com/chengqingtan/luci-app-scutclient)

<u>其中 **scutclient** 和 **luci-app-scutclient** 已被我整合在 [openwrt-scutclient](https://github.com/chengqingtan/openwrt-scutclient)</u>

## 开始编译（以redmi ac 2100为例）

<u>系统使用 ubuntu 20/22 lts</u>

1. 执行以下代码以进行更新

   ```shell
   sudo apt-get update
   sudo apt-get upgrade -y
   ```

2. 然后输入以下命令安装需要的软件

   ```shell
   sudo apt-get -y install build-essential asciidoc binutils bzip2 curl gawk gettext git libncurses5-dev libz-dev patch python3.5 python2.7 unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint device-tree-compiler g++-multilib antlr3 gperf
   ```

3. 克隆源码，`-b 22.03` 指使用 22.03 分支

   ```shell
   git clone -b 22.03 --single-branch https://github.com/Lienol/openwrt lienol22
   ```

4. 执行 `cd lienol22` 进入目录后，修改 **feeds.conf.default** 在最后添加以下几行

   ```
   src-git scut https://github.com/chengqingtan/openwrt-scutclient;main
   src-git kenzo https://github.com/kenzok8/openwrt-packages
   src-git small https://github.com/kenzok8/small
   ```

5. 执行以下命令

   ```shell
   ./scripts/feeds clean
   ./scripts/feeds update -a
   ./scripts/feeds install -a
   ```

6. 执行 `make menuconfig` 以选择需要编译的插件，此时需要将终端最大化

   - **Target System** 指CPU架构，选择 **MediaTek Ralink MIPS**
   - **Subtarget** 指CPU型号，选择 **MT7621 based boards**
   - **Target Profile** 指路由器型号，选择 **Xiaomi Redmi Router AC2100**
   - 添加 **Extra packages->ipv6helper**
   - 添加 **Kernel modules->Netfilter Extensions->kmod->ipt->nat6** (选择 **ipv6helper** 后自动勾选)
   - 添加 **Luci->Applications->luci-app-scutclient**
   - 添加 **Luci->Themes->luci-theme-argon**
   - 添加 **Network->Firewall->ip6tables-mod-nat**
   - 添加 **Network->scutclient** (选择 **luci-app-scutclient** 后自动勾选)

   <u>编辑完成后 exit 退出保存</u>

7. 输入以下命令下载dl库，需要国际上网环境，可以重复执行几遍以确保下载完全

   ```shell
   make -j8 download V=s
   ```

8. 输入以下命令开始编译，-j1指使用1个线程

   ```shell
   make -j1 V=s
   ```

   - 多线程编译使用，尽量不要超过CPU线程数

     ```shell
     make -j8 V=s
     ```

   <u>编译结束后没有Error就编译成功了，文件在 **./bin/targets** 下</u>

9. 重复编译执行以下命令后，重复 6~8步即可

   ```shell
   rm -r ./tmp && rm .config
   ```

   

